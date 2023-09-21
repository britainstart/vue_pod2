<template>
  <div class="hello">
<html lang="en">
  <div id ="card" class = "card">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="styles.css">
    <title>Card Example</title>
</head>
<body>
    <div class = "card">
        <img src="https://www.mydomaine.com/thmb/CaWdFGvTH4-h1VvG6tukpKuU2lM=/3409x0/filters:no_upscale():strip_icc()/binary-4--583f06853df78c6f6a9e0b7a.jpeg"> 
      
        <div class="card-content"> 
          <h4><b>Two Pod Real Estate Agency</b></h4>
            <p id = 'description'> Real Estate Company Focused on delivering the best properties for college students at Penn State University in State College, PA</p> 
      <button class="details-button" id="detailsBtn">Details</button>
      </div>
       </div> 
</body> 
  </div>
  <button id ="btn">Duplicate</button>
  <button id="colorBtn">BGColorChanger</button>
  <button id="Headingbtn">HeadingChanger</button>
  <button id ="dltbtn">DeleteCard</button>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  mounted() {
    document.querySelector('#btn').addEventListener('click', () => {
      const clone = document.querySelector('#card').cloneNode(true); // Clone the whole card
      document.body.appendChild(clone);
    });
    
    var numbers = ["1", "2", "3", "4", "5", "6", "7", "8", "9"];
    var letters = ["A", "B", "C", "D", "E", "F"];
    
    function randomColor() {
      var color = "";
      for (var i = 0; i < 3; i++) {
        var index = Math.floor(Math.random() * (numbers.length + letters.length));
        color += (index < numbers.length) ? numbers[index] : letters[index - numbers.length];
      }
      return color;
    }
    
    document.querySelector('#colorBtn').addEventListener('click', () => {
      const card = document.querySelector('.card');
      // Change background color
      card.style.backgroundColor = '#' + randomColor();
    });
    
    document.querySelector('#Headingbtn').addEventListener('click', () => {
      const title = document.querySelector('h2');
      title.innerText = "Super Pod 2 Realty";
    });
    
    document.querySelector('#dltbtn').addEventListener('click', () => {
      const cards = document.querySelectorAll('.card');
      
      if (cards.length > 2) {
        const lastCard = cards[cards.length - 1];
        lastCard.parentNode.removeChild(lastCard);
      }
    });
    
    var original = document.querySelector('#description').innerText;
    
    document.querySelector('#detailsBtn').addEventListener('click', () => {
      const description = document.querySelector('#description');
      // Toggle the visibility of the description
      if (description.innerText === 'none' || description.innerText === '') {
        description.innerText = original; // Show the description
      } else {
        description.innerText = ''; // Hide the description
      }
    });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.card {
  max-width: 400px;
  margin: 0 auto;
  border: 1px solid #0C0B0B;
  background-color: #0C0B0B;
  padding: 16px;
  display: flex;
  flex-direction: column;
  text-align: center;
}

.card img {
  max-width: 100%;
  height: auto;
}

.card-content {
  flex: 1;
}

/* Style for the Title label */
h2 {
  font-size: 24px;
  margin: -10px 0;
  /* Background color and border */
  background-color: #F8471B;
  /* Background color */
  color: #fff;
  /* Text color on the background */
  padding: 8px 16px;
  border-radius: 4px;
}

p {
  font-size: 16px;
  margin: 8px 0;
  color: #fff;
}

a.details-button {
  background-color: #EA5F0A;
  color: #fff;
  padding: 8px 16px;
  text-decoration: none;
  border-radius: 4px;
}
</style>
