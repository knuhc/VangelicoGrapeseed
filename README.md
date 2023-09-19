
<html>
<head>
  <title>Gem Calculator</title>
    <style>
    body {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 250vh;
      text-align: center;
    }
	.total-box {
		display: flex;
		justify-content: center; /* Center horizontally */
		align-items: center; /* Center vertically */
		margin-top: 20px;
	}}
	
	 .calculate-button {
      width: 150px; /* Adjust the desired width */
      height: 50px; /* Adjust the desired height */
    }
	
	.submit-button {
      width: 150px; /* Adjust the desired width */
      height: 40px; /* Adjust the desired height */
    }
	
	.reset-button {
      width: 150px; /* Adjust the desired width */
      height: 30px; /* Adjust the desired height */
    }
    
    h1 {
      margin-bottom: 20px;
    }
    
    h2 {
      margin-top: 20px;
    }
	
	h3 {
      border: 1px solid black; /* Adjust the border style as needed */
      padding: 5px; /* Add padding to create space around the heading */
    }
    
    .menu-items {
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      gap: 10px;
      margin-bottom: 10px;
    }
    
    .menu-items div {
      display: flex;
      align-items: center;
    }
    
    .total-box {
      display: flex;
      justify-content: flex-end;
      align-self: flex-end;
      margin-top: 20px;
    }
    
    .button-container {
      display: flex;
      gap: 10px;
      margin-top: 20px;
    }
	
	.menu-items div img {
      width: 50px; /* Adjust the desired width */
      height: 50px; /* Adjust the desired height */
      margin-left: 10px; /* Add margin as per your preference */
    }
	
    {
    button {
      margin-top: 20px;
	}}}}}}
  </style>
  <script>
    function calculateTotal() {
    var total = 0;
    var checkboxes = document.querySelectorAll('input[type="checkbox"]:checked');

    checkboxes.forEach(function(checkbox) {
      var quantityInput = checkbox.parentNode.querySelector('input[type="number"]');
      var quantity = parseInt(quantityInput.value);
      var price = parseFloat(checkbox.value);

      if (checkbox.value === '-25%') {
        var itemPrice = total * 0.25;
        total -= itemPrice;
      } else if (checkbox.value === '-30%') {
        var itemPrice = total * 0.3;
        total -= itemPrice;
      } else if (checkbox.value === '-50%') {
        var itemPrice = total * 0.5;
        total -= itemPrice;
      } else {
        total += price * quantity;
      }
    });

    var totalElement = document.getElementById('total');
    totalElement.textContent = total.toFixed(2);

    var discountTotalElement = document.getElementById('discount-total');
    var discount = total * 0.05;
    discountTotalElement.textContent = discount.toFixed(2);
  }


    
    function submitOrder() {
    var name = document.getElementById('name').value;

    // Check if the name field is empty
    if (name.trim() === '') {
      alert('Please enter a name.');
      return;
    }

    var total = parseFloat(document.getElementById('total').textContent);
    var discordWebhookURL = 'https://discord.com/api/webhooks/1118343660623380580/Uhs34Lq96Q3zW5AoKvkOXKLxdqRZJiu1U-B85KW_dR8Sq5nftRKhQNr9BjrgFa75Nbza'; // Replace with your Discord webhook URL

    var xhr = new XMLHttpRequest();
    xhr.open('POST', discordWebhookURL, true);
    xhr.setRequestHeader('Content-Type', 'application/json');

    var message = {
      content: 'Gem Receipt!',
      embeds: [{
        title: 'Order Details',
        fields: [
          {
            name: 'Name',
            value: name,
            inline: true
          },
          {
            name: 'Total',
            value: '$' + total.toFixed(2),
            inline: true
          }
        ]
      }]
    };

    var checkboxes = document.querySelectorAll('input[type="checkbox"]:checked');
    checkboxes.forEach(function (checkbox) {
      var itemLabel = checkbox.nextElementSibling.textContent;
      var quantityInput = checkbox.parentNode.querySelector('input[type="number"]');
      var quantity = parseInt(quantityInput.value);
      var itemTotal = parseFloat(checkbox.value) * quantity;
      message.embeds[0].fields.push({
        name: itemLabel,
        value: 'Quantity: ' + quantity + ', Total: $' + itemTotal.toFixed(2),
        inline: false
      });
    });

    xhr.send(JSON.stringify(message));
  }

  function resetCalculator() {
    var checkboxes = document.querySelectorAll('input[type="checkbox"]');
    var quantityInputs = document.querySelectorAll('input[type="number"]');

    checkboxes.forEach(function (checkbox) {
      checkbox.checked = false;
    });

    quantityInputs.forEach(function (quantityInput) {
      quantityInput.value = 1;
    });

    document.getElementById('total').textContent = '0.00';
  }
  </script>
</head>
<body>
<body style="background-color:White;">
	<img src="BackGround1.png" alt="Company Logo!">
  <h1>Gem Calculator</h1>
  
  
  
  <h3> Opal </h3>
  
  <div>
    <input type="checkbox" id="ColinChoice" value="45">
    <label for="ColinChoice">Opal - Tier 1 (0-30%)</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="JudysChoice" value="120">
    <label for="JudysChoice">Opal - Tier 2 (30-60%)</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="Velmachoice" value="225">
    <label for="Velmachoice">Opal - Tier 3 (60-100%)</label>
    <input type="number" value="1" min="1">
  </div>
  
  <h3> Citrine </h3>
  
  <div>
    <input type="checkbox" id="Davechoice" value="180">
    <label for="Davechoice">Citrine - Tier 1 (0-30%)</label>
    <input type="number" value="1" min="1">
  </div>
  
 <div>
    <input type="checkbox" id="cat10" value="360">
    <label for="cat10">Citrine - Tier 2 (30-60%)</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="cat20" value="720">
    <label for="cat20">Citrine - Tier 3 (60-100%)</label>
    <input type="number" value="1" min="1">
  </div>
  
  <h3> amethyst </h3>
  
  <div>
    <input type="checkbox" id="cat30" value="180">
    <label for="cat30">Amethyst - Tier 1 (0-30%)</label>
    <input type="number" value="1" min="1">
  </div>
  
   <div>
    <input type="checkbox" id="cat50" value="360">
    <label for="cat40">Amethyst - Tier 2 (30-60%)</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="cat100" value="720">
    <label for="cat50">Amethyst - Tier 3 (60-100%)</label>
    <input type="number" value="1" min="1">
  </div>
  
  <h3>sapphire </h3>
  
  <div>
    <input type="checkbox" id="Salad" value="270">
    <label for="Salad">Sapphire - Tier 1 (0-30%)</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="FruitExplosion" value="540">
    <label for="FruitExplosion">Sapphire - Tier 2 (30-60%)</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="TurkeySammie" value="1080">
    <label for="TurkeySammie">Sapphire - Tier 3 (60-100%)</label>
    <input type="number" value="1" min="1">
  </div>
  
  <h3> ruby </h3>
  
   <div>
    <input type="checkbox" id="BeefSammie" value="270">
    <label for="BeefSammie">Ruby - Tier 1 (0-30%)</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="BLTSammie" value="540">
    <label for="BLTSammie">Ruby - Tier 2 (30-60%)</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="choccypanckaes" value="1080">
    <label for="choccypanckaes">Ruby - Tier 3 (60-100%)</label>
    <input type="number" value="1" min="1">
  </div>
  
  <h3> Emerald </h3>
  
  <div>
    <input type="checkbox" id="FrozenYoghurt" value="340">
    <label for="FrozenYoghurt">Emerald - Tier 1 (0-30%)</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="FreshLemonade" value="680">
    <label for="FreshLemonade">Emerald - Tier 2 (30-60%)</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="IcedCoffee" value="1350">
    <label for="IcedCoffee">Emerald - Tier 3 (60-100%)</label>
    <input type="number" value="1" min="1">
  </div>
  
  <h3> Diamond </h3>
  
   <div>
    <input type="checkbox" id="MatchaLatte" value="350">
    <label for="MatchaLatte">Diamond - Tier 1 (0-30%)</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="PumpkinSpiceLate " value="700">
    <label for="PumpkinSpiceLate">Diamond - Tier 2 (30-60%)</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="CatTuccino" value="1400">
    <label for="CatTuccino">Diamond - Tier 3 (60-100%)</label>
    <input type="number" value="1" min="1">
  </div>

  <h3> Gold </h3>
  
   <div>
    <input type="checkbox" id="MatchaLatte" value="150">
    <label for="MatchaLatte">Gold Ore</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="PumpkinSpiceLate " value="200">
    <label for="PumpkinSpiceLate">Gold Bar</label>
    <input type="number" value="1" min="1">
  </div>

  <h3> Silver </h3>
  
   <div>
    <input type="checkbox" id="MatchaLatte" value="75">
    <label for="MatchaLatte">Silver Ore</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="PumpkinSpiceLate " value="100">
    <label for="PumpkinSpiceLate">Silver Bar</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div style="margin-bottom: 100px;"></div>

<div>
    <label for="name">Employee's Name:</label>
    <input type="text" id="name">
  </div>

<div style="margin-bottom: 60px;"></div>

 
<div class="total-box">
  <span>Total: $</span>
  <span id="total">0.00</span>
</div>

 
  
  
  <div style="margin-bottom: 10px;"></div>
  

  
  <div style="margin-bottom: 30px;"></div>

  <button class="calculate-button" onclick="calculateTotal()">Calculate Total</button>
  <button class="submit-button" onclick="submitOrder()">Submit Order</button>
  <button class="reset-button" onclick="resetCalculator()">Reset</button>
  
  
  <div style="margin-bottom: 100px;"></div>
