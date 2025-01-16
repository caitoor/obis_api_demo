<script>
  import { onMount } from "svelte";

  let area = "North Sea"; // Beispielgebiet
  let depth = 50; // Beispielmeerestiefe
  let fishList = [];
  let loading = false;
  let error = null;

  async function fetchFishData() {
    loading = true;
    error = null;
    fishList = [];

    try {
      const response = await fetch(
        `https://api.obis.org/v3/occurrence?area=${encodeURIComponent(
          area,
        )}&depth=${depth}`,
      );

      if (!response.ok) {
        throw new Error(`API error: ${response.statusText}`);
      }

      const data = await response.json();

      fishList = data.results.map((item) => item.scientificName);
    } catch (err) {
      error = err.message;
    } finally {
      loading = false;
    }
  }
</script>

<main>
  <h1>Fish Finder</h1>

  <label>
    Meeresgebiet:
    <input type="text" bind:value={area} placeholder="z.B. North Sea" />
  </label>

  <label>
    Meerestiefe (in Metern):
    <input type="number" bind:value={depth} min="0" />
  </label>

  <button on:click={fetchFishData} disabled={loading}>
    {loading ? "Lädt..." : "Fische suchen"}
  </button>

  {#if error}
    <p class="error">Fehler: {error}</p>
  {/if}

  {#if fishList.length > 0}
    <h2>Gefundene Fische:</h2>
    <ul>
      {#each fishList as fish}
        <li>{fish}</li>
      {/each}
    </ul>
  {:else if !loading}
    <p>Keine Fische gefunden. Versuche es mit anderen Parametern.</p>
  {/if}
</main>

<style>
  .error {
    color: red;
    font-weight: bold;
  }
</style>
