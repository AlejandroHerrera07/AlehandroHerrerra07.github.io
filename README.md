<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="Styles.css">
    <link rel="icon" type="image/jpg" href="favicon-32x32.png"/>
    <title>Mi Applet</title>
</head>
<body>
    <div id="Contenedor">
        
        <div id="Superior">
            <h1 class="Titulo">Applet interactivo de probabilidad</h1>
            <h1 class="Titulo">Temática: Combinatoria</h1>
        </div>

        <div id="Superior">
            <h1 class="Line1">Teoría aplicada:</h1>
            <p id="problema">Entendemos una combinación o combinatoria como la cantidad de combinaciones de tamaño r que podemos
                formar con n elementos. La cantidad de subconjuntos de tamaño r que pertenecen a un conjunto de n objetos está
                denotada por:</p>
            <img src="Combinatoria.png" alt="" width="450px">
        </div>
            
        <div id="Ejercicio">
            <h1 class="Line1" >Problema: </h1>
            <p id="problema">Se ha de realizar un estudio en un hospital para determinar las actitudes de los enfermeros hacia diversos procedimientos administrativos. Se ha de seleccionar una muestra de M enfermeros de entre un total de N enfermeros empleados por el hospital.</p>
            <p id="problema">1) ¿Cuántas muestras diferentes de M enfermeros se pueden seleccionar?</p>
            <p id="problema">2) HT de los N enfermeros son hombres, Si M enfermeros se seleccionan al azar entre los empleados por el hospital, ¿cuál es la probabilidad de que la muestra de M incluirá exactamente H hombres y W mujeres?</p>
            <p id="problema">A continuación se presenta cuatro tarjetas donde se podrán ingresar los datos del problema para generar su solución.</p>
        </div>

    
        <div id="Contenedor-Cards">
            <div class="Card" id="CardSupervisor">
                <h3 class="Titulo">2) Tamaño muestra</h3>
                <p>Ingrese el valor de la variable M</p>
                <input class="entrada" id="muestra" type="number">
                <div class="ContIcon">
                    <img src="https://cdn-icons-png.flaticon.com/512/5266/5266412.png" alt="" width="80" height="80">
                </div>
            </div>

            <div class="Card" id="CardTeamBuilder">
                <h3 class="Titulo">1) Total enfermeros</h3>
                <p>Ingrese el valor de la variable N</p>
                <input class="entrada" id="total" type="number">
                <div class="ContIcon">
                    <img src="https://www.crushpixel.com/big-static18/preview4/diversity-nurse-team-2904875.jpg" alt="" width="80" height="80">
                </div>
            </div>

            <div class="Card" id="CardKarma">
                <h3 class="Titulo">4) Hombres por muestra</h3>
                <p>Ingrese el valor de la variable H</p>
                <input class="entrada" id="hombresM" type="number">
                <div class="ContIcon">
                    <img src="https://cdn-icons-png.flaticon.com/512/2480/2480820.png" alt="" width="80" height="80">
                </div>
            </div>

            <div class="Card" id="CardCalculator">
                <h3 class="Titulo">3) Cantidad total de hombres</h3>
                <p>Ingrese el valor de la variable HT</p>
                <input class="entrada" id="hombresT" type="number">
                <div class="ContIcon">
                    <img src="https://cdn-icons-png.flaticon.com/512/3439/3439472.png" alt="" width="80" height="80">
                </div>
            </div>
        </div>
    </div>
    <div id="info">
    
        <button class="enviar" onclick=calcular()>Calcular</button>
    
        <h1 class="Line2" id="totalGr"></h1>
        <h1 class="Line2" id="combinaciones"></h1>
        <h1 class="Line2" id="probabilidad"></h1>
    </div>

    <div id="Inferior1">
        <h3 class="Titulo1" >Parametrización del ejercicio #55, Sección N° 2. Según orden propuesto en Wackerly & Mendenhall & Scheaffer (7ma ed, 2010, p. 50, edición digital).</h3>
        <h3 class="Titulo1" >Realizada a partir del trabajo entregado por Cristián Rios (20201020107).</h3>
    </div>
    
    <div id="Inferior">
        <h1 class="Titulo1">Universidad distrital Francisco José de caldas</h1>
        <h1 class="Titulo1">Probabilidad (020-81)</h1>
        <h1 class="Titulo1">Holman Alejandro Alarcón Herrera</h1>
        <h1 class="Titulo1">20202020086</h1>
        <h1 class="Titulo1">2023</h1>
    </div>
   


    <script>
        function calcular(){
            let total = document.getElementById('total').value;
            total = parseInt(total);
            let muestra = document.getElementById('muestra').value;
            muestra = parseInt(muestra);
            let hombresM = document.getElementById('hombresM').value;
            hombresM = parseInt(hombresM);
            let hombresT = document.getElementById('hombresT').value;
            hombresT = parseInt(hombresT);
            let mujeresM = muestra - hombresM;
            let totalGr = 1;
            let hombresGr =1;
            let mujeresGr = 1;
            let combinacion = 0;
            let probabilidad = 0;

            totalGr = factorial(total)/(factorial(muestra)*factorial(total-muestra));
            hombresGr = factorial(hombresT)/(factorial(hombresM)*factorial(hombresT-hombresM));
            mujeresGr = factorial(total-hombresT)/(factorial(mujeresM)*factorial(total-hombresT-mujeresM));

            combinacion = hombresGr * mujeresGr;
            probabilidad = (combinacion/totalGr)*100;
            totalGr= totalGr.toFixed(0);
            hombresGr = hombresGr.toFixed(0);
            mujeresGr = mujeresGr.toFixed(0);
            probabilidad = probabilidad.toFixed(3);

            let totalGrupos = document.querySelector("#info > #totalGr");
            totalGrupos.innerHTML = "A) La cantidad de grupos de " + muestra + " enfermeros es de " + totalGr +".";
            let grupos = document.querySelector("#info > #combinaciones");
            grupos.innerHTML = "B) La cantidad de grupos de " + hombresM + " hombres y de " + mujeresM + " mujeres por muestra es de " +combinacion +".";
            let prob = document.querySelector("#info > #probabilidad");
            prob.innerHTML = "B) La probabilidad de una muestra con " + hombresM + " hombres y " + mujeresM + " mujeres es de " + probabilidad + "%.";
            alert("Calculado con éxito");
            
        }

        function factorial(n){
            var total  = 1;
            for (var i=1; i<=n; i++) {
                total = total * i; 
            }
            return total; 
        }
    </script>

</body>
</html>
