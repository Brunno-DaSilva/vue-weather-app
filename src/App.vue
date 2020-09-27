<template>
  <div
    id="app"
    :class="
      typeof weather.main != 'undefined' && weather.main.temp > 16 ? 'warm' : ''
    "
  >
    <main>
      <div class="app__title">
        <img
          src="https://res.cloudinary.com/duprwuo4j/image/upload/v1574831158/Logo/BLOGO_k36v5y.png"
          alt="bruno-logo"
        />
        <h2>Weather APP</h2>
      </div>
      <div class="search-box">
        <input
          v-model="query"
          @keypress="fetchWeatherData"
          type="text"
          class="search-bar"
          placeholder="Search ..."
        />
      </div>

      <div class="weather-wrap" v-if="typeof weather.main != 'undefined'">
        <div class="location-box">
          <div class="location">{{ weather.name }}</div>
          <div class="date">{{ dateBuilder() }}</div>
        </div>

        <div class="weather-box">
          <div class="temp">{{ Math.round(weather.main.temp) }}c</div>
          <div class="weather">{{ weather.weather[0].main }}</div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Kalam:wght@700&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@300&display=swap");

*,
*::after,
*::before {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  font-family: "Roboto", sans-serif;
}
#app {
  background-image: url("./assets/winter.jpg");
  background-size: cover;
  background-position: top;
  transition: ease-in-out 0.5s;
}

#app.warm {
  background-image: url("./assets/summer.jpg");
  background-size: cover;
  background-position: bottom;
  transition: ease-in-out 0.5s;
}

main {
  min-height: 100vh;
  padding: 25px;
  background-image: linear-gradient(
    to bottom,
    rgba(0, 0, 0, 0.25),
    rgba(0, 0, 0, 0.75)
  );
}

.app__title {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  margin: 2rem 0;
}

.app__title h2 {
  font-size: 3rem;
  color: #eeeeee;
  font-family: "Montserrat", sans-serif;
}

.app__title img {
  width: 2.5rem;
  height: auto;
  margin-right: 2rem;
  margin-bottom: 1rem;
}
.search-box {
  width: 100%;
  margin-bottom: 30px;
}
.search-box .search-bar {
  display: block;
  width: 100%;
  padding: 15px;

  color: #313131;
  font-size: 20px;
  appearance: none;
  border: none;
  outline: none;
  background: none;
  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 0px 16px 0px 16px;
  transition: 0.4s;
}
.search-box .search-bar:focus {
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.75);
  border-radius: 16px 0px 16px 0px;
}
.location-box .location {
  color: #fff;
  font-size: 2.2rem;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}
.location-box .date {
  color: #fff;
  font-size: 1;
  font-weight: 300;
  text-align: center;
}
.weather-box {
  text-align: center;
}
.weather-box .temp {
  display: inline-block;
  padding: 10px 25px;
  color: #fff;
  font-size: 102px;
  font-weight: 900;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.25);
  border-radius: 16px;
  margin: 30px 0px;
  box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  letter-spacing: 0.3rem;
}
.weather-box .weather {
  color: #fff;
  font-size: 48px;
  font-weight: 700;
  letter-spacing: 0.1rem;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}
</style>
