<html>
<head>
  <title>Calculadora de Becas y Financiamiento</title>
</head>
<body>
<h1>Calculadora de Becas y Financiamiento Estudiantil</h1>

<form action="" method="get">
  <label>Promedio (0-100):</label><br>
  <input type="number" name="promedio" min="0" max="100"><br><br>

  <label>Costo de colegiatura (Ej.5000):</label><br>
  <input type="number" name="colegiatura" min="0"><br><br>

  <label>Numero de meses a financiar:</label><br>
  <input type="number" name="meses" min="1"><br><br>

  <button type="submit">Calcular</button>
</form>

<script>
  var params = new URLSearchParams(window.location.search);
  var promedio = parseFloat(params.get('promedio'));
  var colegiatura = parseFloat(params.get('colegiatura'));
  var meses = parseInt(params.get('meses'));

  if (!isNaN(promedio) && !isNaN(colegiatura)) {

    document.write('<hr>');
    document.write('<h2>Resultados</h2>');
    document.write('<p>Promedio ingresado: ' + promedio + '</p>');
    document.write('<p>Colegiatura: $' + colegiatura.toFixed(2) + '</p>');

    if (promedio >= 95) {
      var descuento = colegiatura * 1.00;
      var aPagar = colegiatura - descuento;
      document.write('<p>Beca obtenida: 100%</p>');
      document.write('<p>Descuento: $' + descuento.toFixed(2) + '</p>');
      document.write('<p>Total a pagar: $' + aPagar.toFixed(2) + '</p>');
    } else if (promedio >= 90) {
      var descuento = colegiatura * 0.80;
      var aPagar = colegiatura - descuento;
      document.write('<p>Beca obtenida: 80%</p>');
      document.write('<p>Descuento: $' + descuento.toFixed(2) + '</p>');
      document.write('<p>Total a pagar: $' + aPagar.toFixed(2) + '</p>');
    } else if (promedio > 85) {
      var descuento = colegiatura * 0.60;
      var aPagar = colegiatura - descuento;
      document.write('<p>Beca obtenida: 60%</p>');
      document.write('<p>Descuento: $' + descuento.toFixed(2) + '</p>');
      document.write('<p>Total a pagar: $' + aPagar.toFixed(2) + '</p>');
    } else {
      document.write('<p>No calificas para beca. Promedio minimo requerido: 86</p>');
      document.write('<h2>Plan de Financiamiento</h2>');

      if (!isNaN(meses) && meses >= 1) {
        var totalSinInteres = colegiatura;
        var totalConInteres = colegiatura * 1.05;
        var mensualidadSin = totalSinInteres / meses;
        var mensualidadCon = totalConInteres / meses;

        document.write('<p>Meses: ' + meses + '</p>');
        document.write('<p>Total sin interes: $' + totalSinInteres.toFixed(2) + '</p>');
        document.write('<p>Mensualidad sin interes: $' + mensualidadSin.toFixed(2) + '</p>');
        document.write('<p>Total con interes (5%): $' + totalConInteres.toFixed(2) + '</p>');
        document.write('<p>Mensualidad con interes: $' + mensualidadCon.toFixed(2) + '</p>');
      } else {
        document.write('<p>Ingresa el numero de meses para calcular el financiamiento.</p>');
      }
    }
  }
</script>

