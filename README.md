<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Menu Calculator</title>
    <style>
        body {
            text-align: center;
            padding: 20px; /* Add padding to the body */
			background-color: #963264;
        }

        .category {
            float: left;
            margin-right: 20px;
			margin-left: 60px;
        }

        .item {
            margin-bottom: 10px;
        }

        h2, #total, #subtotal, #commission {
            text-align: center;
        }

        .bottom-row {
            text-align: center;
            margin-top: 20px;
        }
		.menu-image {
            width: 100%; /* Set the width of the image to 100% of its container */
        }
    </style>
</head>

<body>
	
    <form id="menuForm">
        <div class="category">
            <h2>Specials</h2>
            <div class="item">
                <label><input type="checkbox" class="appetizer" value="1500"> UWU Daddy special</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
            <div class="item">
                <label><input type="checkbox" class="appetizer" value="1500"> UWU Mommy Special</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
            <div class="item">
                <label><input type="checkbox" class="appetizer" value="250"> Basic Bitch Special</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
        </div>

        <div class="category">
            <h2>Combo's</h2>
            <div class="item">
                <label><input type="checkbox" class="main-dish" value="300"> Colin's Choice</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
            <div class="item">
                <label><input type="checkbox" class="main-dish" value="300"> Judy's Choice</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
			<div class="item">
                <label><input type="checkbox" class="main-dish" value="300"> Velma's Choice</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
            <div class="item">
                <label><input type="checkbox" class="main-dish" value="300"> Dave's Choice</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
        </div>

        

        <div class="category">
            <h2>Entree</h2>
            <div class="item">
                <label><input type="checkbox" class="drink" value="150"> Salad</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
            <div class="item">
                <label><input type="checkbox" class="drink" value="200"> Fruit Explosion</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
			<div class="item">
                <label><input type="checkbox" class="drink" value="150"> Sandwhiches</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
            <div class="item">
                <label><input type="checkbox" class="drink" value="175"> Choccy Pancakes</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
        </div>  

        <div class="category">
            <h2>Dessert</h2>
            <div class="item">
                <label><input type="checkbox" class="salad" value="125"> Homemade Cat Cookie</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
            <div class="item">
                <label><input type="checkbox" class="salad" value="125"> Apple Crumble</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
			<div class="item">
                <label><input type="checkbox" class="salad" value="125"> Cat Donut</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
            <div class="item">
                <label><input type="checkbox" class="salad" value="125"> Cat Cupcake</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
        </div>

        <div class="category">
            <h2>Delivery</h2>
            <div class="item">
                <label><input type="checkbox" class="pizza" value="250"> City Delivery</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
            <div class="item">
                <label><input type="checkbox" class="pizza" value="500"> Sandy Delivery</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
			<div class="item">
                <label><input type="checkbox" class="pizza" value="750"> Paleto Delivery</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
        </div>
		
	
				
		
        <div class="category">
            <h2>Misc Items</h2>
            <div class="item">
                <label><input type="checkbox" class="sandwich" value="5000"> Mystery Box</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
			<div class="item">
                <label><input type="checkbox" class="sandwich" value="2500"> Cardboard Box</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
           
			
        </div>
		
		<div class="category">
            <h2>Cat Tuccino Special's</h2>
            <div class="item">
                <label><input type="checkbox" class="dessert" value="1600"> 10 for 1600$</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
            <div class="item">
                <label><input type="checkbox" class="dessert" value="2500"> 20 for 2500$</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
			<div class="item">
                <label><input type="checkbox" class="dessert" value="3500"> 30 for 3500$</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
            <div class="item">
                <label><input type="checkbox" class="dessert" value="4500"> 40 for 4500$</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
			<div class="item">
                <label><input type="checkbox" class="dessert" value="5500"> 50 for 5500$</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
            <div class="item">
                <label><input type="checkbox" class="dessert" value="9000"> 100 for 9000$</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
        </div>
		
				<div class="category">
            <h2>Beverage</h2>
            <div class="item">
                <label><input type="checkbox" class="soup" value="125"> Frozen Yoghurt</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
            <div class="item">
                <label><input type="checkbox" class="soup" value="200"> Fresh Lemonade</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
			<div class="item">
                <label><input type="checkbox" class="soup" value="125"> Iced Coffee</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
            <div class="item">
                <label><input type="checkbox" class="soup" value="125"> Matcha Latte</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
			<div class="item">
                <label><input type="checkbox" class="soup" value="125"> Pumpkin Spice Latte</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
            <div class="item">
                <label><input type="checkbox" class="soup" value="200"> Cat Tuccino</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
			<div class="item">
                <label><input type="checkbox" class="soup" value="125"> Bobba Tea</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
            <div class="item">
                <label><input type="checkbox" class="soup" value="125"> Green Tea</label>
                <input type="number" class="quantity" value="1" min="1">
            </div>
        </div>
		
		

        <div style="clear:both;"></div> <!-- Clear float -->
		
		  <div style="margin-bottom: 30px;"></div>
		
		<!-- Employee Name Input Field -->
            <div class="employee-name-input">
				<label for="employeeName">Employee Name:</label>
				<input type="text" id="employeeName" name="employeeName" required>
			</div>
			
			  <div style="margin-bottom: 10px;"></div>

        <div class="bottom-row">
            
            <h2>Total: $<span id="subtotal">0.00</span></h2>
            <h2>Commission (10%): $<span id="commission">0.00</span></h2>
            <h2>Discount Amount: $<span id="discountAmount">0.00</span></h2>
			
			<!-- Discount Options -->
            <input type="radio" name="discount" value="25"> 25% Off
            <input type="radio" name="discount" value="30"> 30% Off
            <input type="radio" name="discount" value="50"> 50% Off

            
			
			  <div style="margin-bottom: 20px;"></div>
			
			  

            <input type="submit" value="Submit Order">
			<button type="button" id="calculateBtn">Calculate Total</button>
        </div>
    </form>

    <!-- ... (your existing HTML code) ... -->

<script>
        // JavaScript code
        const checkboxes = document.querySelectorAll('input[type="checkbox"]');
const quantities = document.querySelectorAll('.quantity');
const calculateBtn = document.getElementById('calculateBtn');
const subtotalDisplay = document.getElementById('subtotal');
const commissionDisplay = document.getElementById('commission');
const discountAmountDisplay = document.getElementById('discountAmount');
const totalDisplay = document.getElementById('subtotal'); // Changed to subtotal, assuming it's the total before applying discount and commission
const menuForm = document.getElementById('menuForm');
const employeeNameInput = document.getElementById('employeeName');
const discountOptions = document.getElementsByName('discount');

calculateBtn.addEventListener('click', calculateTotal);

function calculateTotal() {
    let subtotal = 0;
    let itemsOrdered = [];

    checkboxes.forEach((checkbox, index) => {
        if (checkbox.checked) {
            const itemPrice = parseFloat(checkbox.value);
            const quantity = parseInt(quantities[index].value);
            subtotal += itemPrice * quantity;
            itemsOrdered.push(checkbox.parentElement.innerText.trim());
        }
    });

    const commission = subtotal * 0.1;
    let selectedDiscount = 0;
    for (let i = 0; i < discountOptions.length; i++) {
        if (discountOptions[i].checked) {
            selectedDiscount = parseFloat(discountOptions[i].value);
            break;
        }
    }

    const discountPercentage = selectedDiscount / 100;
    const discountAmount = subtotal * discountPercentage;

    const total = subtotal - discountAmount;

    subtotalDisplay.textContent = subtotal.toFixed(2);
    commissionDisplay.textContent = commission.toFixed(2);
    discountAmountDisplay.textContent = discountAmount.toFixed(2);
    totalDisplay.textContent = total.toFixed(2);

    return { itemsOrdered, subtotal, commission, discountAmount, total };
}

function resetMenu() {
    checkboxes.forEach(checkbox => {
        checkbox.checked = false;
    });

    quantities.forEach(quantityInput => {
        quantityInput.value = 1;
    });
}

menuForm.addEventListener('submit', function (event) {
    event.preventDefault();

    const employeeName = employeeNameInput.value;
    const { itemsOrdered, subtotal, selectedDiscount, commission, discountAmount, total } = calculateTotal();

    const data = {
        content: 'New Order!',
        embeds: [{
            title: 'Order Details',
            color: 0xFF5733,
            fields: [
                {
                    name: 'Name',
                    value: employeeName,
                    inline: true
                },
                {
                    name: 'Total',
                    value: '$' + total.toFixed(2),
                    inline: true
                },
                {
                    name: 'Discount Total',
                    value: '$' + discountAmount.toFixed(2),
                    inline: true
                },
                {
                    name: 'Discount Applied',
                    value: selectedDiscount + '%',
                    inline: true
                },
                {
                    name: 'Commission (10%)',
                    value: '$' + commission.toFixed(2),
                    inline: true
                },
                {
                    name: 'Ordered Items',
                    value: itemsOrdered.join('\n'),
                    inline: false
                }
            ]
        }]
    };

    // Discord Webhook URL (replace with your actual webhook URL)
    const webhookUrl = 'https://discord.com/api/webhooks/1157451563212750959/FqNuldbbd1b4cZOxmo3xsbngVnMEWZfOSyXxwtwMuv7iTmeLhgDbL6maZiZJnfgYgVwy';

    fetch(webhookUrl, {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
        },
        body: JSON.stringify(data),
    })
        .then(response => {
            if (!response.ok) {
                throw new Error('Network response was not ok');
            }
            console.log('Order details sent successfully to Discord.');
        })
        .catch(error => {
            console.error('There has been a problem with your fetch operation:', error);
        });

    // Reset menu items and quantities after submitting the order
    resetMenu();

    // Clear the employee name input field
    employeeNameInput.value = '';
});
    </script>
</body>

</html>







