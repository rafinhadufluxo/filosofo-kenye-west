<template>
  <div>
    <div class="row">

      <div class="column">
        <img src="https://www.pngmart.com/files/16/American-Rapper-Kanye-West-PNG-Transparent-Image.png"
          class="card-img-top" alt="figure poke" width="300"/>
      </div>

      <div class="column" @click="reloadPage">
        <p>
          {{ frase.quote }}
        </p>
        <button class="button" @click="reloadPage">Next</button>
        
      </div>
     
    </div>

  </div>
</template>


<script>
import axios from "axios";

export default {

  data() {
    return {
      frase: "",
      
    };
  },
  created() {
    this.getUser();
  },
  methods: {

    getUser() {
      axios
        .get("https://api.kanye.rest/")
        .then((res) => {
          this.frase = res.data;
          console.log(this.frase);
        })
        .catch((error) => {
          console.log(error);
        });
    },

    reloadPage() {
      window.location.reload();
    },
  },
};
</script>

<style>
/* html,
body {
  min-height: 100%;
} */
body {
  min-height: 100vh;
  background-color: #282c34; 
}

* {
  box-sizing: border-box;
}

.row {
  margin-top: 15%;
  /* display: flex; */
  /* align-items: center; */
  margin-left: auto;
  margin-right: auto;
  width: 54vw;
  padding: 0% 0% 0% 10%;
}

/* Create three equal columns that floats next to each other */
.column {
  float: left;
  width: 33.33%;
  padding: 15px;
  margin-top: 5%;
}

/* Clear floats after the columns */
.row::after {
  content: "";
  display: table;
  clear: both;
}
p {
  color: white;
  font-size: 1.2rem;
}
.button {
  background-color: #4CAF50;
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin-top: 15%;
  margin-right: 30%;
}

/* Responsive layout - makes the three columns stack on top of each other instead of next to each other */
@media screen and (max-width:600px) {

  .column {
    float: left;
    width: 78.33vw;
    padding: 15px;
  }

  .row {
    margin-top: 15%;
    /* display: flex; */
    /* align-items: center; */
    /* margin-left: auto; */
    /* margin-right: auto; */
    width: 100vw;
    padding: 0% 0% 0% 15%;

  }
  .button {
    background-color: #4CAF50;
    border: none;
    color: white;
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
    margin-top: 15%;
    margin-right: 20vw;
    margin-left: 20vw;
  }
}
</style>

