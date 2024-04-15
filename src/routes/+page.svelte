<div class="flex-row-container">
  <div class="flex-row-item">
    <h2>Schedule:</h2>
    <iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vR5i_a8bhOM55AVsqXyqDKrUzDHv4mIJ3YEzxXKblQjOEXIEDTCQS3Ml-rIm_mPZcxc6Dd_HIwpPgQ3/pubhtml?gid=0&amp;single=true&amp;widget=true&amp;headers=false&amp;wmode=opaque" width="100%" data-embed="true" height="800px"></iframe>    
  </div>

  <div class="flex-row-item" style="max-width: 25vw">
    <div style="margin-top: 50%; border: solid; border-radius: 30px; padding: 10px;">
      <h1>Welcome to .Astronomy 13!</h1>
      <p>Please sign up to the Slack!<br>(see emails for invite link)</p>
    </div>
  </div>

  <div class="flex-row-item" style="overflow-y: scroll">
    <h2>Bluesky posts with #dotastro</h2>
    <bsky-embed
      search="#astronomy"
      mode="dark"
      limit="20"
      link-target="_blank"
      link-image="false"
      custom-styles={""}
    />
  </div>
</div>

<style>
  p {
    font-size: 2em;
    text-align: center;
  }
  h1 {
    font-size: 3em;
    text-align: center;
  }
  h2 {
    font-size: 2em;
    text-align: center;
  }

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
    flex: 1 0 30%; /*grow | shrink | basis */
    height: 100vh;
  }

  .flex-row-item {
    border: 20px;
    /* background-color: white; */
    border-color: white;
    margin-left: 40px;
    margin-right: 80px;
  }
</style>
