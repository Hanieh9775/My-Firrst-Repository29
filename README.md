<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>QR Code Generator</title>

    body {
        background: #0d0d0d;
        display: flex;
        height: 100vh;
        justify-content: center;
        align-items: center;
        color: #fff;
        font-family: "Poppins", sans-serif;
        margin: 0;
    }
    
        width: 380px;
        background: #141414;
        padding: 30px;
        border-radius: 20px;
        text-align: center;
        box-shadow: 0 0 25px #00eaff;
        animation: fadeIn .6s ease;
    }
    h2 {
        color: #00eaff;
        font-size: 24px;
        margin-bottom: 20px;
    }
    input {
        width: 85%;
        padding: 12px;
        border-radius: 8px;
        border: none;
        outline: none;
        margin-bottom: 15px;
        font-size: 16px;
    }
    button {
        width: 90%;
        padding: 12px;
        border-radius: 8px;
        border: none;
        background: #00eaff;
        color: #000;
        font-weight: bold;
        cursor: pointer;
        transition: .3s;
        font-size: 16px;
    }
    button:hover {
        background: #009ebc;input
    }
    #qrBox {
        margin-top: 20px;
        padding: 15px;
        background: #1c1c1c;
        border-radius: 15px;
        display: inline-block;
        box-shadow: 0 0 15px #00eaff;
        min-height: 150px;
    }
    @keyframes fadeIn {
        from {opacity: 0; transform: translateY(20px);}
        to {opacity: 1; transform: translateY(0);}
    }
</style>
</head>
<body>

<div class="box">
    <h2>QR Code Generator</h2>
    <input type="text" id="text" placeholder="Enter text or URL...">
    <button onclick="generateQR()">Generate QR Code</button>
    <div id="qrBox"></div>
</div>

<script>
function generateQR() {
    const text = document.getElementById("text").value.trim();
    const qrBox = document.getElementById("qrBox");

    if (text === "") {
        qrBox.innerHTML = "<p>Please enter something!</p>";
        return;
    }

    const encoded = encodeURIComponent(text);
    const qrUrl = `https://api.qrserver.com/v1/create-qr-code/?size=220x220&data=${encoded}`;

    qrBox.innerHTML = `<img src="${qrUrl}" style="width:220px;border-radius:10px;">`;
}
</script>

</body>
</html>
