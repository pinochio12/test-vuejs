<template>
    <div id="app">
      <h1 v-if="!selectedPokemon">Pokémon Pokedex</h1>
      <button @click="fetchData" class="fetch-button" v-if="!selectedPokemon">Get Pokémon Dex</button>
      <button @click="resetView" class="back-button" v-if="selectedPokemon">Back to List</button>
  
      <div v-if="pokemonList.length && !selectedPokemon" class="pokemon-grid">
        <div v-for="(pokemon, index) in pokemonList" :key="pokemon.name" class="pokemon-card" @click="selectPokemon(pokemon)">
          <img :src="pokemon.image" alt="Pokemon image" class="pokemon-image" />
          <h3 class="pokemon-name">{{ pokemon.name }}</h3>
          <p>Type: <span class="pokemon-type">{{ pokemon.types.join(', ') }}</span></p>
          <p>HP: {{ pokemon.stats.hp }}</p>
          <p>Attack: {{ pokemon.stats.attack }}</p>
          <p>Defense: {{ pokemon.stats.defense }}</p>
        </div>
      </div>
  
      <div v-if="selectedPokemon" class="selected-pokemon">
        <h2>Selected Pokémon: {{ selectedPokemon.name }}</h2>
        <div class="pokemon-card selected-card">
          <img :src="selectedPokemon.image" alt="Selected Pokemon image" class="pokemon-image" />
          <h3 class="pokemon-name">{{ selectedPokemon.name }}</h3>
          <p>Type: <span class="pokemon-type">{{ selectedPokemon.types.join(', ') }}</span></p>
          <p>HP: {{ selectedPokemon.stats.hp }}</p>
          <p>Attack: {{ selectedPokemon.stats.attack }}</p>
          <p>Defense: {{ selectedPokemon.stats.defense }}</p>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import axios from "axios";
  
  export default {
    data() {
      return {
        pokemonList: [],
        selectedPokemon: null
      };
    },
    methods: {
      async fetchData() {
        try {
          const response = await axios.get("https://pokeapi.co/api/v2/pokemon?offset=0&limit=151");
          const pokemonData = response.data.results;
          const detailedPokemonList = await Promise.all(
            pokemonData.map(async (pokemon) => {
              const pokemonDetails = await axios.get(pokemon.url);
              const pokemonInfo = pokemonDetails.data;
  
              return {
                name: pokemonInfo.name.toUpperCase(),
                image: pokemonInfo.sprites.front_default,
                types: pokemonInfo.types.map((type) => type.type.name),
                stats: {
                  hp: pokemonInfo.stats[0].base_stat,
                  attack: pokemonInfo.stats[1].base_stat,
                  defense: pokemonInfo.stats[2].base_stat,
                }
              };
            })
          );
  
          this.pokemonList = detailedPokemonList;
          this.selectedPokemon = null;
        } catch (error) {
          console.error("Error fetching Pokémon data:", error);
        }
      },
      selectPokemon(pokemon) {
        this.selectedPokemon = pokemon;
      },
      resetView() {
        this.selectedPokemon = null;
      }
    }
  };
  </script>
  
  <style>
  body {
    font-family: 'Arial', sans-serif;
    background-color: #f4f4f4;
    margin: 0;
    padding: 0;
  }
  
  #app {
    text-align: center;
    padding: 20px;
  }
  
  h1 {
    font-size: 2.5rem;
    margin-bottom: 20px;
    color: #3a3a3a;
  }
  
  .fetch-button, .back-button {
    background-color: #4CAF50;
    border: none;
    color: white;
    padding: 10px 20px;
    text-align: center;
    font-size: 1rem;
    cursor: pointer;
    border-radius: 5px;
    transition: background-color 0.3s;
    margin: 10px;
  }
  
  .fetch-button:hover, .back-button:hover {
    background-color: #45a049;
  }
  
  .pokemon-grid {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 20px;
  }
  
  .pokemon-card {
    background-color: white;
    border-radius: 15px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    width: 200px;
    padding: 20px;
    text-align: center;
    transition: transform 0.2s, box-shadow 0.2s;
    cursor: pointer;
  }
  
  .pokemon-card:hover {
    transform: scale(1.05);
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
  }
  
  .pokemon-image {
    width: 120px;
    height: 120px;
    margin-bottom: 10px;
  }
  
  .pokemon-name {
    font-size: 1.2rem;
    color: #333;
    margin-bottom: 10px;
  }
  
  .pokemon-type {
    font-weight: bold;
    color: #3a3a3a;
  }
  
  .selected-pokemon {
    margin-top: 50px;
  }
  
  .selected-card {
    background-color: #ffeb3b;
    padding: 30px;
    border-radius: 20px;
  }
  
  @media (max-width: 768px) {
    .pokemon-grid {
      flex-direction: column;
      align-items: center;
    }
  
    .pokemon-card {
      width: 90%;
    }
  }
  </style>
  