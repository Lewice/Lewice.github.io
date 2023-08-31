
<html>
<head>
  <title>Menu Calculator</title>
    <style>
    body {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 350vh;
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
      align-self: Center;
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
    var discount = total * 0.08;
    discountTotalElement.textContent = discount.toFixed(2);
  }


    
    function submitOrder() {
    var name = document.getElementById('name').value;
    if (name.trim() === '') {
      alert('Please enter a name.');
      return;
    }

    // Collect selected items and their quantities
    var selectedItems = [];
    var checkboxes = document.querySelectorAll('input[type="checkbox"]:checked');
    checkboxes.forEach(function (checkbox) {
      var itemName = checkbox.nextElementSibling.textContent;
      var quantityInput = checkbox.parentNode.querySelector('input[type="number"]');
      var quantity = parseInt(quantityInput.value);
      var price = parseFloat(checkbox.value);
      selectedItems.push({ name: itemName, quantity: quantity, price: price });
    });

    var total = 0;
    var discountTotal = 0;

    selectedItems.forEach(function (item) {
      if (item.price < 0) {
        var discountPercentage = Math.abs(item.price);
        var itemDiscount = total * (discountPercentage / 100);
        discountTotal += itemDiscount;
      } else {
        total += item.price * item.quantity;
      }
    });

    var commission = (total * 0.08).toFixed(2);
    var totalWithDiscount = total - discountTotal;

    alert('Order submitted!');

    var discordWebhookURL = 'https://discord.com/api/webhooks/1115717872002551860/QeP0olu8qsHp7pE0XxHqB7dTK2c9i7hqA1vX4LB8ogLAw14NBj08zLN--8K9hvHeB0hO';

    var xhr = new XMLHttpRequest();
    xhr.open('POST', discordWebhookURL, true);
    xhr.setRequestHeader('Content-Type', 'application/json');

    var message = {
      content: 'New order!',
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
            value: '$' + totalWithDiscount.toFixed(2),
            inline: true
          },
          {
            name: 'Discount Total',
            value: '$' + discountTotal.toFixed(2),
            inline: true
          },
          {
            name: 'Commission (8%)',
            value: '$' + commission,
            inline: true
          },
          {
            name: 'Ordered Items',
            value: selectedItems.map(item => `${item.name} x${item.quantity} - $${(item.price * item.quantity).toFixed(2)}`).join('\n'),
            inline: false
          }
        ]
      }]
    };

    xhr.send(JSON.stringify(message));
  }

function resetCalculator() {
  var checkboxes = document.querySelectorAll('input[type="checkbox"]');
  var quantityInputs = document.querySelectorAll('input[type="number"]');
  
  checkboxes.forEach(function(checkbox) {
    checkbox.checked = false;
  });
  
  quantityInputs.forEach(function(quantityInput) {
    quantityInput.value = 1;
  });
  
  document.getElementById('total').textContent = '0.00';
}
	function submitAndReset() {
	submitOrder();
	resetCalculator();
}

  </script>
</head>
<body>
	
<div style="margin-bottom: 25px;"></div>
 
<body style="background-color:deeppink;">
	<img src="BackGround.png" alt="Company Logo!">
  <h1>Menu Calculator</h1>
  
  <h2>Menu Items</h2>

  <div style="margin-bottom: 10px;"></div>
  
  <h3>Specials</h3>

  <div style="margin-bottom: 10px;"></div>
  
  <div>
    <input type="checkbox" id="uwueats" value="1200$">
    <label for="Velmachoice">UWU Eats - 1200$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="Davechoice" value="1500$">
    <label for="Davechoice">Uwu Daddy Specials - 1500$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="Davechoice" value="1500$">
    <label for="Davechoice">UWU Mommy Special - 1500$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="Davechoice" value="250">
    <label for="Davechoice">Hot Gworl Special - 250$</label>
    <input type="number" value="1" min="1">
  </div>

  <!--This is where you change the combos with prices-->
  
  
  <h3> Combos </h3>
  
  <div>
    <input type="checkbox" id="ColinChoice" value="300"><!--The price is the value, change that and then the name and itll change on the menu-->
    <label for="ColinChoice">Colin's Choice - 300$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="JudysChoice" value="300">
    <label for="JudysChoice">Judy's Choice - 300    $</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="Velmachoice" value="300$">
    <label for="Velmachoice">Velma's choice - 300$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="Davechoice" value="300$">
    <label for="Davechoice">Daves's Choice - 300$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div style="margin-bottom: 10px;"></div>
 
 
 <h3> Cat Tuccino Specials </h3>
 <div>
    <input type="checkbox" id="cat10" value="1600">
    <label for="cat10">10 for 1600$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="cat20" value="2500">
    <label for="cat20">20 for 2500$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="cat30" value="3500">
    <label for="cat30">30 for 3500$</label>
    <input type="number" value="1" min="1">
  </div>

  <div>
    <input type="checkbox" id="cat30" value="4500">
    <label for="cat40">40 for 4500$</label>
    <input type="number" value="1" min="1">
  </div>
  
   <div>
    <input type="checkbox" id="cat50" value="5500">
    <label for="cat50">50 for 5500$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="cat100" value="9000">
    <label for="cat50">100 for 9000$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div style="margin-bottom: 10px;"></div>
  

  
   <h3> Entree </h3>
  
  <div>
    <input type="checkbox" id="Salad" value="150">
    <label for="Salad">Salad - 150$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="FruitExplosion" value="200">
    <label for="FruitExplosion">Fruit Explosion - 200$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="TurkeySammie" value="150">
    <label for="TurkeySammie">Turkey Sammie - 150$</label>
    <input type="number" value="1" min="1">
  </div>
  
   <div>
    <input type="checkbox" id="BeefSammie" value="150$">
    <label for="BeefSammie">Beef Sammie - 150$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="BLTSammie" value="150">
    <label for="BLTSammie">Blt Sammie - 150$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="choccypanckaes" value="175">
    <label for="choccypanckaes">Choccy Panckaes - 175$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div style="margin-bottom: 10px;"></div>
  
  
  <h3> Beverage </h3>
  
  <div>
    <input type="checkbox" id="FrozenYoghurt" value="125">
    <label for="FrozenYoghurt">Frozen Yoghurt - 125$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="FreshLemonade" value="200">
    <label for="FreshLemonade">Fresh Lemonade - 200$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="IcedCoffee" value="125">
    <label for="IcedCoffee">Iced Coffee - 125$</label>
    <input type="number" value="1" min="1">
  </div>
  
   <div>
    <input type="checkbox" id="MatchaLatte" value="125">
    <label for="MatchaLatte">Matcha Latte - 125$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="PumpkinSpiceLate " value="125">
    <label for="PumpkinSpiceLate">Pumpkin Spice Late  - 125$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="CatTuccino" value="200">
    <label for="CatTuccino">Cat Tuccino - 200$</label>
    <input type="number" value="1" min="1">
  </div>
  
<div>
    <input type="checkbox" id="BobbaTea " value="125">
    <label for="BobbaTea">Bobba Tea  - 125$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="GreenTea" value="125">
    <label for="GreenTea">Green Tea - 125$</label>
    <input type="number" value="1" min="1">
  </div>
  
  
  <div style="margin-bottom: 10px;"></div>
  
    <h3> Dessert </h3>
  
  <div>
    <input type="checkbox" id="HomemadeCatCookie" value="125">
    <label for="HomemadeCatCookie">Homemade Cat Cookie - 125$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="AppleCrumble" value="125">
    <label for="AppleCrumble">Apple Crumble - 125$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="CatDonut" value="125">
    <label for="CatDonut">Cat Donut - 125$</label>
    <input type="number" value="1" min="1">
  </div>
  
<div>
    <input type="checkbox" id="CatCupcake" value="125">
    <label for="CatCupcake">Cat Cupcake - 125$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div style="margin-bottom: 10px;"></div>
  
  <h3> Delivery </h3>
  
  <div>
    <input type="checkbox" id="CityDelivery" value="250">
    <label for="CityDelivery">City Delivery - 250$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="Sandy" value="500">
    <label for="Sandy">Sandy Delivery - 500$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div>
    <input type="checkbox" id="Paleto" value="750">
    <label for="Paleto">Paleto Delivery - 750$</label>
    <input type="number" value="1" min="1">
  </div>
  
  <div style="margin-bottom: 10px;"></div>
  

<div style="margin-bottom: 10px;"></div>
  
  <h3> Discount Items</h3> 
  <div>
  <input type="checkbox" id="25off" value="-25%">
  <label for="25off">Mech, EMS, LEO Disount - 25% off </label>
  <input type="number" value="1" min="1" max="1">
</div>

<div>
  <input type="checkbox" id="30off" value="-30%">
  <label for="30off">Non Fresh Items - 30% off</label>
  <input type="number" value="1" min="1" max="1">
</div>

<div>
  <input type="checkbox" id="50off" value="-50%">
  <label for="50off">Employee Discount - 50% off</label>
  <input type="number" value="1" min="1" max="1">
</div>

<h3>Misc.</h3>

<div>
  <input type="checkbox" id="MysteryGift" value="5000" >
  <label for="MysteryBox">Mystery Gift - $5000</label>
  <input type="number" value="1" min="1">
</div>

<div>
  <input type="checkbox" id="MysteryGift" value="2500" >
  <label for="MysteryBox">Mystery Gift(50% off) - $2500</label>
  <input type="number" value="1" min="1">
</div>

<div style="margin-bottom: 100px;"></div>

<div>
    <label for="name">Employee's Name:</label>
    <input type="text" id="name">
  </div>
  <p><b> Include Kitchen and Front staff in names section </b></p>

<div style="margin-bottom: 25px;"></div>
 
<div class="total-box">
  <span>Total: $</span>
  <span id="total">0.00</span>
</div>

<div class="total-box">
  <span>Commision (8%): $</span>
  <span id="discount-total">0.00</span>
</div>




 
  
  
  <div style="margin-bottom: 45px;"></div>
  

  <button class="calculate-button" onclick="calculateTotal()">Calculate Total</button>
  <button class="submit-button" onclick="submitAndReset()">Submit Order</button>
  <button class="reset-button" onclick="resetCalculator()">Reset</button>

 
  
  
  <div style="margin-bottom: 10px;"></div>
