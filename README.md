<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Menu Calculator and Form Submission</title>
  <script src="https://code.jquery.com/jquery-3.4.1.js" integrity="sha256-WpOohJOqMqqyKL9FccASB9O0KwACQJpFTUBLTYOVvVU=" crossorigin="anonymous"></script>
  <style>
    body, h2, form, label, p, button, select, input {
      font-size: 10;
      margin-right: 10px; /* Add a margin for spacing */
    }

    label {
      display: inline-block; /* Display as inline-block to make items appear beside each other */
      margin-bottom: 5px;
    }

    body, h2, form {
      text-align: center;
    }

    p {
      text-align: center;
      margin: 0; /* Remove default margin for <p> */
    }

    button {
      margin-top: 10px;
    }
	body {
	background-color: grey;
	}
  </style>
  <script>
    function calculateTotals() {
  let total = 0;

  // Calculate total from selected items
  const menuItems = document.querySelectorAll('.menu-item:checked');
  menuItems.forEach(item => {
    const price = parseFloat(item.dataset.price);
    const quantity = parseInt(item.nextElementSibling.value);

    if (!isNaN(price) && !isNaN(quantity) && quantity > 0) {
      // Exclude "Mystery Box" from discounts
      if (item.classList.contains('exclude-discount')) {
        total += price * quantity;
      } else {
        total += price * quantity * (1 - ($("#discount").val() / 100));
      }
    }
  });

  // Change commission rate from 5% to 10%
  const commission = total * 0.10;

  document.getElementById('total').innerText = total.toFixed(2);
  document.getElementById('commission').innerText = commission.toFixed(2);
}

    function SubForm() {
  // Check if the employee name is provided
  const employeeName = $("#employeeName").val();
  if (employeeName.trim() === "") {
    alert("Employee Name is required!");
    return;
  }

  // Get selected menu items and quantities
  const orderedItems = [];
  const menuItems = document.querySelectorAll('.menu-item:checked');
  menuItems.forEach(item => {
    const itemName = item.parentNode.textContent.trim();
    const price = parseFloat(item.dataset.price);
    const quantity = parseInt(item.nextElementSibling.value);

    if (!isNaN(price) && !isNaN(quantity) && quantity > 0) {
      orderedItems.push({
        name: itemName,
        price: price,
        quantity: quantity
      });
    }
  });

  // Calculate total and commission
  const total = parseFloat($("#total").text());
  const commission = parseFloat($("#commission").text());
  const discount = parseFloat($("#discount").val());

  // Prepare data for API submission
  const formData = {
    "Employee Name": employeeName,
    "Total": total.toFixed(2),
    "Commission": commission.toFixed(2),
    "Items Ordered": JSON.stringify(orderedItems),
    "Discount Applied": discount
  };

  // Form Submission Logic for Spreadsheet
  $.ajax({
    url: "https://api.apispreadsheets.com/data/wy0vT9JJYGL6a8IZ/",
    type: "post",
    data: formData,
    headers: {
      accessKey: "c9d38abe3a9ed79cd6f8d878d8986f6f",
      secretKey: "fb1fe402814e22e7a92cb48ce0937cb0",
      "Content-Type": "application/x-www-form-urlencoded",
    },
    success: function () {
      alert("Form Data Submitted to Spreadsheet and Discord :)");
      resetForm();
    },
    error: function () {
      alert("There was an error :(");
    }
  });
  // Prepare data for Discord webhook
  const discordData = {
  username: "Menu Order Bot",
  content: `New order submitted by ${employeeName}`,
  embeds: [{
    title: "Order Details",
    fields: [
      { name: "Employee Name", value: employeeName, inline: true },
      { name: "Total", value: `$${total.toFixed(2)}`, inline: true },
      { name: "Commission", value: `$${commission.toFixed(2)}`, inline: true },
      { name: "Discount Applied", value: `${discount}%`, inline: true },
      { name: "Items Ordered", value: orderedItems.map(item => `${item.quantity}x ${item.name}`).join('\n') }
    ],
    color: 0x00ff00 // You can customize the color
  }]
};

  // Form Submission Logic for Spreadsheet
  $.ajax({
    url: "https://api.apispreadsheets.com/data/bviQcW5QzAlYop7f/",
    type: "post",
    data: {
      "Employee Name": employeeName,
      "Total": total.toFixed(2),
      "Commission": commission.toFixed(2),
      "Items Ordered": JSON.stringify(orderedItems),
      "Discount Applied": discount
    },
    success: function () {
      alert("Form Data Submitted to Spreadsheet and Discord :)");
      // Reset the form after submission
      resetForm();
    },
    error: function () {
      alert("There was an error :(");
    }
  });

  // Form Submission Logic for Discord webhook
  $.ajax({
    url: "https://discord.com/api/webhooks/1157451563212750959/FqNuldbbd1b4cZOxmo3xsbngVnMEWZfOSyXxwtwMuv7iTmeLhgDbL6maZiZJnfgYgVwy",
    type: "post",
    contentType: "application/json",
    data: JSON.stringify(discordData),
    success: function () {
      // Do nothing specific for Discord success
    },
    error: function () {
      console.error("Error sending data to Discord :(");
    }
  });
}

    function resetForm() {
      // Reset checkboxes and quantity inputs
      $('.menu-item').prop('checked', false);
      $('.quantity').val(1);

      // Reset totals
      document.getElementById('total').innerText = '';
      document.getElementById('commission').innerText = '';
      // Reset discount dropdown to default
      $("#discount").val("0");
    }
  </script>
</head>
<body>

  <h2>Uwu Menu</h2>

  <form id="menuForm">
  <h3>Specials</h3>
    <label>
      <input type="checkbox" class="menu-item" data-price="1500"> Uwu Daddy Special - $1500
      <input type="number" class="quantity" value="1" min="1">
    </label>
    <label>
      <input type="checkbox" class="menu-item" data-price="1500"> Uwu Mommy Special - $1500
      <input type="number" class="quantity" value="1" min="1">
    </label>
    <label>
      <input type="checkbox" class="menu-item" data-price="250"> Basic Bitch Special - $250
      <input type="number" class="quantity" value="1" min="1">
    </label>
	
	<h3>Specials</h3>
    <label>
      <input type="checkbox" class="menu-item" data-price="300"> Colin's Choice - $300
      <input type="number" class="quantity" value="1" min="1">
    </label>
    <label>
      <input type="checkbox" class="menu-item" data-price="300"> Judy's Choice - $300
      <input type="number" class="quantity" value="1" min="1">
    </label>
    <label>
      <input type="checkbox" class="menu-item" data-price="300"> Velma's Choice - $300
      <input type="number" class="quantity" value="1" min="1">
    </label>
	<label>
      <input type="checkbox" class="menu-item" data-price="300"> Dave's Choice - $300
      <input type="number" class="quantity" value="1" min="1">
    </label>
	
	<h3>Entree</h3>
    <label>
      <input type="checkbox" class="menu-item" data-price="150"> Salad - $150
      <input type="number" class="quantity" value="1" min="1">
    </label>
    <label>
      <input type="checkbox" class="menu-item" data-price="200"> Fruit Explosion - $200
      <input type="number" class="quantity" value="1" min="1">
    </label>
    <label>
      <input type="checkbox" class="menu-item" data-price="150"> Sandwhiches - $150
      <input type="number" class="quantity" value="1" min="1">
    </label>
	<label>
      <input type="checkbox" class="menu-item" data-price="175"> Choccy Pancakes - $175
      <input type="number" class="quantity" value="1" min="1">
    </label>
	
	<h3>Desserts</h3>
    <label>
      <input type="checkbox" class="menu-item" data-price="125"> Homemade Cat Cookies - $125
      <input type="number" class="quantity" value="1" min="1">
    </label>
    <label>
      <input type="checkbox" class="menu-item" data-price="125"> Apple Crumble - $125
      <input type="number" class="quantity" value="1" min="1">
    </label>
    <label>
      <input type="checkbox" class="menu-item" data-price="125"> Cat Donut - $125
      <input type="number" class="quantity" value="1" min="1">
    </label>
	<label>
      <input type="checkbox" class="menu-item" data-price="125"> Cat Cupcake - $125
      <input type="number" class="quantity" value="1" min="1">
    </label>
	
	<h3>Delivery</h3>
    <label>
      <input type="checkbox" class="menu-item" data-price="250"> City Delivery - $250
      <input type="number" class="quantity" value="1" min="1">
    </label>
    <label>
      <input type="checkbox" class="menu-item" data-price="500"> Sandy Delivery - $500
      <input type="number" class="quantity" value="1" min="1">
    </label>
    <label>
      <input type="checkbox" class="menu-item" data-price="750"> Poleto Delivery - $750
      <input type="number" class="quantity" value="1" min="1">
    </label>
	
	<h3>Misc Items</h3>
    <label>
      <input type="checkbox" class="menu-item exclude-discount" data-price="5000"> Mystery Box - $5000
      <input type="number" class="quantity" value="1" min="1">
    </label>
    <label>
      <input type="checkbox" class="menu-item" data-price="2500"> Box's - $2500
      <input type="number" class="quantity" value="1" min="1">
    </label>
	
	<h3>Cattacino Specials</h3>
    <label>
      <input type="checkbox" class="menu-item" data-price="1600"> 10 for 1600$ 
      <input type="number" class="quantity" value="1" min="1">
    </label>
    <label>
      <input type="checkbox" class="menu-item" data-price="2500"> 20 for 2500$
      <input type="number" class="quantity" value="1" min="1">
    </label>
	<label>
      <input type="checkbox" class="menu-item" data-price="3500"> 30 for 3500$
      <input type="number" class="quantity" value="1" min="1">
    </label>
    <label>
      <input type="checkbox" class="menu-item" data-price="4500"> 40 for 4500$
      <input type="number" class="quantity" value="1" min="1">
    </label>
	<label>
      <input type="checkbox" class="menu-item" data-price="5500"> 50 for 5500$
      <input type="number" class="quantity" value="1" min="1">
    </label>
    <label>
      <input type="checkbox" class="menu-item" data-price="9000"> 100 for 9000$
      <input type="number" class="quantity" value="1" min="1">
    </label>
	
	<h3>Beverages</h3>
    <label>
      <input type="checkbox" class="menu-item" data-price="125"> Frozen Yoghurt - $125
      <input type="number" class="quantity" value="1" min="1">
    </label>
    <label>
      <input type="checkbox" class="menu-item" data-price="200"> Fresh Lemonade - $200
      <input type="number" class="quantity" value="1" min="1">
    </label>
	<label>
      <input type="checkbox" class="menu-item" data-price="125"> Iced Coffee - $125
      <input type="number" class="quantity" value="1" min="1">
    </label>
    <label>
      <input type="checkbox" class="menu-item" data-price="125"> Matcha Latte - $125
      <input type="number" class="quantity" value="1" min="1">
    </label>
	<label>
      <input type="checkbox" class="menu-item" data-price="125"> Pumpkin Spice Latte - $125
      <input type="number" class="quantity" value="1" min="1">
    </label>
    <label>
      <input type="checkbox" class="menu-item" data-price="200"> Cat Tuccino - $200
      <input type="number" class="quantity" value="1" min="1">
    </label>
	<label>
      <input type="checkbox" class="menu-item" data-price="125"> Bobba Tea - $125
      <input type="number" class="quantity" value="1" min="1">
    </label>
    <label>
      <input type="checkbox" class="menu-item" data-price="125"> Green Tea - $125
      <input type="number" class="quantity" value="1" min="1">
    </label>
	

	
	
	
	
	
	<div style="margin-bottom: 30px;"></div>
	
	<label for="discount">Select Discount:</label>
    <select id="discount" onchange="calculateTotals()">
      <option value="0">No Discount</option>
      <option value="25">25% Discount</option>
      <option value="30">30% Discount</option>
      <option value="50">50% Discount</option>
    </select>
	
	<div style="margin-bottom: 30px;"></div>
	


    <label for="employeeName">Employee Name:</label>
    <input type="text" id="employeeName" required>
	
	<div style="margin-bottom: 30px;"></div>
	
	

    <p>Total: $<span id="total"></span></p>
    <p>Commission (10%): $<span id="commission"></span></p>
	
	<div style="margin-bottom: 30px;"></div>

    <button type="button" onclick="calculateTotals()">Calculate</button>
    <button type="button" onclick="SubForm()">Submit</button>
    <button type="button" onclick="resetForm()">Reset</button>
  </form>

</body>
</html>
