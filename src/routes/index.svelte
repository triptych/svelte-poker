<script context="module">
  export async function preload(page, session) {
    const tables = await this.fetch(process.env.API_URL+`/tables.json`).then((res) => res.json())
    return { tables }
  }
</script>

<script>
export let tables;
</script>

<style>
.lobby {
  background: url('/felt.png');
  height: 100%;
  text-align: center;
}
</style>

<div class="lobby">
  <h1>Rock Solid Poker</h1>

  {#each tables as table}
    <div class="table">
      <a href="/tables/{table.id}">Table {table.id} - {table.settings.small_blind_amount} / {table.settings.big_blind_amount}</a>
    </div>
  {/each}
</div>