<script>
  export let sheet;

  function filterRow(row) {
    const rowLength = row.length;
    const indexOfLastGoodValue = row
      .slice(1)
      .reduce(
        (previousBestIndex, value, currentIndex) =>
          value === "" ? previousBestIndex : currentIndex + 1,
        1
      );
    const colspan = Math.floor(rowLength / indexOfLastGoodValue);
    const rowShouldBeHighlighted = row.some((value) => /\blunch\b|\bbreak\b|\bdinner\b/.test(value.toLowerCase()));
    return {
      data: row.slice(0, indexOfLastGoodValue + 1),
      colspan: colspan,
      style: rowShouldBeHighlighted ? "background-color: #004765;" : ""
    };
  }

  $: heading = sheet === undefined ? undefined : filterRow(sheet[0]);
  $: rows =
    sheet === undefined ? undefined : sheet.slice(1).map((row) => filterRow(row));
</script>

<table>
  <thead>
    <tr>
      {#each heading.data as value, index}
        <th colspan={index === 0 ? 1 : heading.colspan}>{value}</th>
      {/each}
    </tr>
  </thead>
  <tbody>
    {#each rows as row}
      <tr>
        {#each row.data as value, index}
          <td colspan={index === 0 ? 1 : row.colspan} style={row.style}>{value}</td>
        {/each}
      </tr>
    {/each}
  </tbody>
</table>

<style>
  table {
    width: 100%;
    border-collapse: collapse;
    border: 1px solid;
  }
  tr {
    border-top: 1px solid;
    border-bottom: 1px solid;
  }
  td:nth-child(1) {
    background-color: #004765;
    width: 100px;
    text-align: center;
    border-right: 1px solid;
  }
  th {
    background-color: #004765;
  }
  th:nth-child(1) {
    border-right: 1px solid;
  }
  th,
  td {
    border-right: 1px solid;
    padding: 5px;
    text-align: center;
  }
</style>
