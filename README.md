<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Lector de Código de Barras</title>

<script src="https://unpkg.com/html5-qrcode"></script>

<style>
body{
    font-family: Arial, sans-serif;
    text-align:center;
    background:#f5f5f5;
    padding:20px;
}

h1{
    color:#333;
}

#reader{
    width:350px;
    margin:auto;
}

.resultado{
    margin-top:20px;
    padding:15px;
    background:white;
    border-radius:10px;
    box-shadow:0 2px 5px rgba(0,0,0,.2);
}

.codigo{
    font-size:24px;
    font-weight:bold;
    color:#007bff;
}
</style>
</head>

<body>

<h1>📷 Lector de Código de Barras</h1>

<div id="reader"></div>

<div class="resultado">
    <h3>Código Detectado:</h3>
    <div id="codigo" class="codigo">Esperando lectura...</div>
</div>

<script>

function onScanSuccess(decodedText, decodedResult) {

    document.getElementById("codigo").innerText = decodedText;

    navigator.vibrate?.(200);

    console.log(decodedResult);
}

const html5QrCodeScanner = new Html5QrcodeScanner(
    "reader",
    {
        fps: 10,
        qrbox: 250,
        formatsToSupport: [
            Html5QrcodeSupportedFormats.EAN_13,
            Html5QrcodeSupportedFormats.EAN_8,
            Html5QrcodeSupportedFormats.UPC_A,
            Html5QrcodeSupportedFormats.UPC_E,
            Html5QrcodeSupportedFormats.CODE_128,
            Html5QrcodeSupportedFormats.CODE_39,
            Html5QrcodeSupportedFormats.QR_CODE
        ]
    }
);

html5QrCodeScanner.render(onScanSuccess);

</script>

</body>
</html>
