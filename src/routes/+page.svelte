<script>
  import Schedule from "../lib/Schedule.svelte";
  import BlueskyFeed from "../lib/BlueskyFeed.svelte";
</script>

<div class="flex-row-container">
  <div class="flex-row-item" style="max-width: 350px;">
    <img src="ESA_logo_White.png" alt="ESA logo in white" width="70%" />
    <img src="dotlogo_white.png" alt="ESA logo in white" width="100%" />
    <p>ESAC, Madrid | April 2024</p>
    <p>dotastronomy.com/thirteen</p>
  
    <div class="notice" style="margin-bottom: auto;">
      <h2>Day 0</h2>
      <p>Today is <strong>tutorial</strong> day!</p>
    </div>
  
    <div class="notice" style="margin-bottom: auto;">
      <h2>Slack</h2>
      <p>Please sign up to the Slack! (see emails for invite link)</p>
    </div>

    
  </div>

  <div class="flex-row-item" style="overflow-y: scroll;">
    <Schedule
      url="https://docs.google.com/spreadsheets/d/1cidiHSAld6RSVhiZKTZc7eD0CgyqwptE987R__eW9cM/gviz/tq?tqx=out:csv&sheet=Public"
      start={new Date(2024, 3, 23)}
      columnRanges={[
        [1, 5],
        [5, 9],
        [9, 12],
        [12, 15],
      ]}
    />
    <!-- <iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vR5i_a8bhOM55AVsqXyqDKrUzDHv4mIJ3YEzxXKblQjOEXIEDTCQS3Ml-rIm_mPZcxc6Dd_HIwpPgQ3/pubhtml?gid=0&amp;single=true&amp;widget=true&amp;headers=false&amp;wmode=opaque" width="100%" height="850px" data-embed="true"></iframe>     -->
  </div>

  <div class="flex-row-item" style="overflow-y: scroll;">
    <BlueskyFeed search="#dotastro"/>
    
  </div>
</div>

<style>
  .flex-row-container {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-around;
    width: 95%;
    margin-left: auto;
    margin-right: auto;
  }

  /* Large */
  .flex-row-container {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-around;
    width: 95%;
    margin-left: auto;
    margin-right: auto;
  }

  .flex-row-container > .flex-row-item {
    flex: 1 1 50%; /*grow | shrink | basis */
    height: 100vh;
  }

  .flex-row-item {
    /* background-color: white; */
    border-color: white;
    padding-left: 80px;
    padding-right: 80px;
  }

  @media all and (min-width: 800px) {
    .flex-row-item:not(:last-child) {
      border-right: solid 2px;
    }
  }

  /* Medium screens */
  /* @media all and (max-width: 800px) {
    .flex-row-container {
      justify-content: space-around;
    }
    .flex-row-item {
      border-color: white;
      padding-left: 20px;
      padding-right: 20px;
    }
  } */

  /* Small screens */
  @media all and (max-width: 800px) {
    .flex-row-container {
      /* On small screens, we are no longer using row direction but column */
      flex-direction: column;
    }

    .flex-row-item {
      border-right: solid 0px;
      padding-bottom: 50px;
      padding-left: 20px;
      padding-right: 20px;
    }
  }

  .notice {
    /* background-color: #ffffff;
    color: #003247; */
    border: solid 2px;
    border-radius: 30px;
    padding: 10px;
    margin-top: 50px;
  }

  img {
    padding: 20px;
    display: block;
    margin-left: auto;
    margin-right: auto;
  }
</style>
