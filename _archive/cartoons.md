<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>My Cartoons</title>
<style>
    body {
        font-family: 'Times New Roman', Times, serif;
        margin: 0;
        padding: 0;
        background-color: #fafafa;
    }
    .container {
        width: 80%;
        margin: auto;
        background-color: #fff;
        padding: 20px;
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }
    .header {
        text-align: center;
        border-bottom: 1px solid #ddd;
        padding-bottom: 10px;
        margin-bottom: 20px;
    }
    .cartoon {
        width: 100%;
        max-width: 600px;
        margin: auto;
        display: block;
    }
    .navigation {
        text-align: center;
        margin-top: 20px;
    }
    button {
        padding: 10px 20px;
        margin: 0 10px;
        background-color: #333;
        color: white;
        border: none;
        cursor: pointer;
    }
    button:hover {
        background-color: #555;
    }
</style>
</head>
<body>

<div class="container">
    <div class="header">
        <h1>My Cartoon Collection</h1>
    </div>
    <img src="assets/cartoon1.jpg" alt="Cartoon" class="cartoon" id="cartoonImage">
    <div class="navigation">
        <button onclick="prevCartoon()">Previous</button>
        <button onclick="nextCartoon()">Next</button>
    </div>
</div>

<script>
    var currentCartoon = 1;
    var totalCartoons = 10; // Update this to your total number of cartoons

    function nextCartoon() {
        if(currentCartoon < totalCartoons) {
            currentCartoon++;
            updateCartoon();
        }
    }

    function prevCartoon() {
        if(currentCartoon > 1) {
            currentCartoon--;
            updateCartoon();
        }
    }

    function updateCartoon() {
        var image = document.getElementById('cartoonImage');
        image.src = 'assets/cartoon' + currentCartoon + '.jpg';
    }
</script>

</body>
</html>
