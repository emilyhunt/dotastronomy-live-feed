<script>
  import { onMount } from "svelte";
  import Papa from "papaparse";
  import Table from "./Table.svelte";
  export let url = "";
  export let start = new Date();
  export let end = new Date();
  export let timeColumn = 0;
  export let columnRanges = [];
  let sheet = undefined;

  function getTodayDateIndex() {
    const today = new Date();
    if (today < start) {
      return 0;
    }

    // https://stackoverflow.com/questions/3224834/get-difference-between-2-dates-in-javascript
    const diffTime = Math.abs(today - start);
    const diffDays = Math.floor(diffTime / (1000 * 60 * 60 * 24));

    // If we're past the end of the conference
    if (diffDays >= columnRanges.length) {
      return columnRanges.length - 1
    }

    return diffDays;
  }

  function getTodayOnly(sheet) {
    const columnsToUse = columnRanges[getTodayDateIndex()];
    let data = sheet.data
      .map((row) =>
        row
          .slice(timeColumn, timeColumn + 1)
          .concat(row.slice(columnsToUse[0], columnsToUse[1]))
      )
      .map((row) => row.map((value) => cleanValue(value)));
    data[0][0] = "Time";
    data = removeEmptyRowsAndColumns(data);
    return data;
  }

  function cleanValue(value) {
    return value.replace("\n", "").trim();
  }

  function removeEmptyRowsAndColumns(array) {
    // Rows with no data
    array = array.filter((row) => !row.slice(1).every((value) => value === ""))

    // Empty columns (more complicated as we have to check everything)
    const goodColumns = Array(array[0].length).fill(false);
    array.map((row) =>
      row.map(
        (value, index) => (goodColumns[index] = goodColumns[index] | (value !== ""))
      )
    );
    array = array.map((row) => row.filter((value, index) => goodColumns[index]));

    return array;
  }

  onMount(async () => {
    const result = await fetch(url);
    sheet = await result
      .text()
      .then((text) => Papa.parse(text))
      .then((text) => getTodayOnly(text));
  });
</script>

<h2>Schedule:</h2>

{#if sheet}
  <Table {sheet} />
{:else}
  <p>Loading schedule...</p>
{/if}
