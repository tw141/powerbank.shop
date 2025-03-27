# powerbank.shop
<!DOCTYPE html>
<html lang="nl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Plakbare Powerbanks</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; background: #f4f4f4; margin: 0; padding: 20px; }
        .container { max-width: 800px; margin: auto; background: white; padding: 20px; border-radius: 10px; box-shadow: 0 0 10px rgba(0, 0, 0, 0.1); }
        .product { border: 1px solid #ddd; padding: 20px; margin: 20px 0; border-radius: 5px; background: #fff; text-align: left; }
        .product img { max-width: 100%; height: auto; border-radius: 5px; display: block; margin-bottom: 10px; }
        .paypal-button-container { margin-top: 10px; }
        button { background: blue; color: white; padding: 10px; border: none; cursor: pointer; border-radius: 5px; width: 100%; font-size: 16px; }
        button:hover { background: darkblue; }
        .form-section { margin-top: 20px; padding: 15px; background: #fff; border-radius: 5px; box-shadow: 0 0 5px rgba(0, 0, 0, 0.1); text-align: left; }
        form input, form button { margin-top: 10px; display: block; width: calc(100% - 20px); padding: 10px; border: 1px solid #ddd; border-radius: 5px; }
        form button { background: green; }
        form button:hover { background: darkgreen; }
    </style>
</head>
<body>
    <div class="container">
        <h1>Plakbare Powerbanks</h1>
        <p>De handigste powerbanks die je direct op je telefoon kunt plakken.</p>
        
        <div class="product">
            <h2>Stick Powerbank 5000mAh</h2>
            <img src="powerbank5000.jpg" alt="Stick Powerbank 5000mAh">
            <p>Draadloos opladen, compact formaat, sterke plakkracht.</p>
            <p><strong>Prijs: €29,99</strong></p>
            <div id="paypal-button-5000"></div>
        </div>

        <div class="product">
            <h2>Stick Powerbank 10000mAh</h2>
            <img src="powerbank10000.jpg" alt="Stick Powerbank 10000mAh">
            <p>Meer capaciteit voor langere gebruikstijd.</p>
            <p><strong>Prijs: €39,99</strong></p>
            <div id="paypal-button-10000"></div>
        </div>

        <div class="form-section">
            <h2>Verzendgegevens</h2>
            <form id="order-form">
                <input type="text" placeholder="Naam" required>
                <input type="email" placeholder="E-mail" required>
                <input type="text" placeholder="Adres" required>
                <input type="text" placeholder="Postcode" required>
                <input type="text" placeholder="Stad" required>
                <button type="submit">Bestelling bevestigen</button>
            </form>
        </div>
    </div>

    <script src="https://www.paypal.com/sdk/js?client-id=YOUR_PAYPAL_CLIENT_ID&currency=EUR"></script>
    <script>
        function createPayPalButton(id, amount, itemName) {
            paypal.Buttons({
                style: { layout: 'vertical', color: 'blue', shape: 'rect', label: 'paypal' },
                createOrder: function(data, actions) {
                    return actions.order.create({
                        purchase_units: [{
                            amount: { value: amount },
                            description: itemName
                        }]
                    });
                },
                onApprove: function(data, actions) {
                    return actions.order.capture().then(function(details) {
                        alert('Betaling voltooid door ' + details.payer.name.given_name);
                    });
                }
            }).render(id);
        }

        createPayPalButton('#paypal-button-5000', '29.99', 'Stick Powerbank 5000mAh');
        createPayPalButton('#paypal-button-10000', '39.99', 'Stick Powerbank 10000mAh');
    </script>
</body>
</html>
