<!DOCTYPE html>
<html>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<head>
  <title>Prueba websevice</title>
</head>
<body>
  <input type="text" class="text-box-centrado" id="codigo" placeholder="Código del artículo" value="2.1529.016.0">
  <button onclick="info()">Consultar</button>
  <p>Resultado: <span id="resultado"></span></p>

  <script>
    function info() {
    var texto = document.getElementById("codigo").value;
    fetch('http://tractoricambi.dyn.grn.es:8075/info_articulo?codigo=' + texto)
      .then(response => response.text())
      .then(data => {
        console.log('Respuesta del servidor:', data);
        document.getElementById("resultado").innerText = data;
      })
      .catch(error => {
        console.error('Error:', error);
      });
    }
  </script>
</body>
</html>
