<script>
  const url = "https://weatherapi-com.p.rapidapi.com/current.json?q=Bogot%C3%A1";
  const options = {
    method: "GET",
    headers: {
      "x-rapidapi-key": "da0b98c9ecmshfc9de67ef37e13bp1a76b1jsned82bc52b1cd",
      "x-rapidapi-host": "weatherapi-com.p.rapidapi.com",
    },
  };

  const getWeather = fetch(url, options)
    .then(res => res.json())
    .then(res => {
      const {location, current } = res;
      const {country, localtime, name, region, lat, lon} = location;
      const {temp_c, wind_kph, humidity} = current.condition;
      return {country, localtime, name, region, lat, lon, temp_c, wind_kph, humidity};
    });
</script>

{#await getWeather then }
  {console.log(getWeather)}
{/await}

<h1>Welcome to SvelteKit</h1>
<p>
  Visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to read the
  documentation
</p>

<style>
  * {
    font-family:
      system-ui,
      -apple-system,
      BlinkMacSystemFont,
      "Segoe UI",
      Roboto,
      Oxygen,
      Ubuntu,
      Cantarell,
      "Open Sans",
      "Helvetica Neue",
      sans-serif;
  }
</style>
