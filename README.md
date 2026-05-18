# batcave-system
Public
<<!DOCTYPE html>
<html lang="es">

<head>

    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>BATCAVE SYSTEM</title>

    <style>

        *{
            margin:0;
            padding:0;
            box-sizing:border-box;
        }

        body{

            font-family:Arial;
            background-image:url('https://images.unsplash.com/photo-1506744038136-46273834b3fb?q=80&w=1400&auto=format&fit=crop');

            background-size:cover;
            background-position:center;
            height:100vh;
            overflow:hidden;
            color:white;
            transition:0.5s;

        }

        .overlay{

            background:rgba(0,0,0,0.75);
            width:100%;
            height:100vh;
            padding:20px;

        }

        .titulo{

            text-align:center;
            margin-top:20px;

        }

        .titulo h1{

            font-size:60px;
            color:cyan;
            text-shadow:0 0 20px cyan;

        }

        .titulo p{

            color:lightgray;
            font-size:22px;
            margin-top:10px;

        }

        .panel{

            width:95%;
            max-width:1100px;
            margin:auto;
            margin-top:20px;

            background:rgba(0,0,0,0.6);

            border:2px solid cyan;
            border-radius:20px;

            padding:20px;

            box-shadow:0 0 30px cyan;

        }

        #estado{

            text-align:center;
            font-size:28px;
            margin-bottom:20px;

        }

        .stats{

            display:flex;
            justify-content:space-around;
            flex-wrap:wrap;

            font-size:20px;

            margin-bottom:20px;

        }

        .botones{

            text-align:center;

        }

        button{

            padding:15px 20px;
            margin:10px;

            border:none;
            border-radius:12px;

            background:cyan;
            color:black;

            font-size:18px;
            font-weight:bold;

            cursor:pointer;
            transition:0.3s;

        }

        button:hover{

            transform:scale(1.1);
            background:white;

        }

        #juego{

            width:100%;
            height:320px;

            background:#111;

            border:2px solid white;
            border-radius:15px;

            margin-top:20px;

            position:relative;
            overflow:hidden;

        }

        .criminal{

            width:70px;
            height:70px;

            border-radius:50%;

            position:absolute;

            display:flex;
            justify-content:center;
            align-items:center;

            font-size:35px;

            cursor:pointer;

            background:red;

            transition:0.2s;

        }

        .criminal:hover{

            transform:scale(1.2);

        }

        #mensaje{

            text-align:center;
            margin-top:20px;
            font-size:25px;
            color:orange;

        }

        #reloj{

            text-align:center;
            margin-top:15px;

            font-size:28px;
            color:lime;

        }

        #login{

            position:fixed;
            top:0;
            left:0;

            width:100%;
            height:100%;

            background:black;

            display:flex;
            justify-content:center;
            align-items:center;
            flex-direction:column;

            z-index:9999;

        }

        #login h1{

            color:cyan;
            font-size:60px;

            text-shadow:0 0 20px cyan;

        }

        #clave{

            padding:15px;
            width:320px;

            font-size:20px;

            border:none;
            border-radius:10px;

            margin-top:20px;

            text-align:center;

        }

        #error{

            color:red;
            margin-top:20px;
            font-size:22px;

        }

    </style>

</head>

<body>

    <!-- LOGIN -->

    <div id="login">

        <h1>🦇 BATCAVE ACCESS</h1>

        <input
        type="password"
        id="clave"
        placeholder="Ingrese contraseña">

        <br><br>

        <button onclick="verificarClave()">
            INGRESAR
        </button>

        <p id="error"></p>

    </div>

    <!-- SISTEMA -->

    <div class="overlay">

        <div class="titulo">

            <h1>🦇 BATCAVE SYSTEM</h1>

            <p>JARVIS conectado a Gotham City</p>

        </div>

        <div id="reloj"></div>

        <div class="panel">

            <div id="estado">
                Esperando órdenes del señor Wayne...
            </div>

            <div class="stats">

                <div>
                    🎯 Criminales atrapados:
                    <span id="puntos">0</span>
                </div>

                <div>
                    ⚡ Energía:
                    <span id="energia">100</span>%
                </div>

            </div>

            <!-- BOTONES -->

            <div class="botones">

                <button onclick="iniciarMision()">
                    🚓 Iniciar misión
                </button>

                <button onclick="modoAlerta()">
                    🚨 Alerta
                </button>

                <button onclick="activarBatmovil()">
                    🏎 Batimóvil
                </button>

                <button onclick="hackearCamara()">
                    📹 Hackear
                </button>

                <button onclick="activarModoNoche()">
                    🌙 Sigilo
                </button>

                <button onclick="llamarAlfred()">
                    ☕ Alfred
                </button>

                <button onclick="activarIA()">
                    🤖 IA
                </button>

                <button onclick="abrirArsenal()">
                    🦾 Arsenal
                </button>

                <button onclick="activarArmadura()">
                    🛡 Armadura
                </button>

                <button onclick="usarBatarang()">
                    🦇 Batarang
                </button>

                <button onclick="villanoFinal()">
                    💀 Joker
                </button>

                <button onclick="recargar()">
                    ⚡ Recargar
                </button>

            </div>

            <!-- JUEGO -->

            <div id="juego"></div>

            <div id="mensaje">
                Gotham está tranquila...
            </div>

        </div>

    </div>

    <script>

        let puntos = 0;
        let energia = 100;

        // LOGIN

        function verificarClave(){

            let clave =
            document.getElementById("clave").value;

            if(clave === "oswaldo"){

                document.getElementById("login").style.display =
                "none";

                alert("🦇 Batman es Oswaldo");

                document.getElementById("estado").innerHTML =
                "🦇 Acceso total concedido";

            }

            else{

                document.getElementById("error").innerHTML =
                "❌ Contraseña incorrecta";

            }

        }

        // MISION

        function iniciarMision(){

            document.getElementById("estado").innerHTML =
            "🚓 Patrullando Gotham";

            crearCriminal();

        }

        function crearCriminal(){

            if(energia <= 0){

                document.getElementById("mensaje").innerHTML =
                "❌ Sin energía";

                return;

            }

            let criminal =
            document.createElement("div");

            criminal.classList.add("criminal");

            criminal.innerHTML = "😈";

            let juego =
            document.getElementById("juego");

            let x =
            Math.random() * 900;

            let y =
            Math.random() * 230;

            criminal.style.left = x + "px";
            criminal.style.top = y + "px";

            criminal.onclick = function(){

                puntos++;
                energia -= 10;

                document.getElementById("puntos").innerHTML =
                puntos;

                document.getElementById("energia").innerHTML =
                energia;

                document.getElementById("mensaje").innerHTML =
                "✅ Criminal atrapado";

                criminal.remove();

                setTimeout(crearCriminal,700);

            }

            juego.appendChild(criminal);

        }

        // MODOS

        function modoAlerta(){

            document.body.style.backgroundImage =
            "url('https://images.unsplash.com/photo-1519608487953-e999c86e7455?q=80&w=1400&auto=format&fit=crop')";

            document.getElementById("estado").innerHTML =
            "🚨 ALERTA EN GOTHAM";

        }

        function activarBatmovil(){

            document.getElementById("mensaje").innerHTML =
            "🏎 Batimóvil desplegado";

        }

        function hackearCamara(){

            document.getElementById("mensaje").innerHTML =
            "📹 Cámaras hackeadas";

            document.getElementById("juego").style.border =
            "4px solid lime";

        }

        function activarModoNoche(){

            document.body.style.filter =
            "brightness(70%)";

            document.getElementById("estado").innerHTML =
            "🌙 Modo sigilo";

        }

        function llamarAlfred(){

            let frases = [

                "☕ Café listo señor Wayne",
                "📡 Gotham monitoreada",
                "🛠 Traje reparado",
                "🦇 Alfred está listo"

            ];

            let random =
            frases[Math.floor(Math.random()*frases.length)];

            document.getElementById("mensaje").innerHTML =
            random;

        }

        function activarIA(){

            document.getElementById("estado").innerHTML =
            "🤖 IA ACTIVADA";

            document.getElementById("juego").style.boxShadow =
            "0 0 30px cyan";

        }

        // ARSENAL

        function abrirArsenal(){

            alert(

            "🦾 ARSENAL DISPONIBLE\n\n" +

            "🦇 Batarangs\n" +
            "💣 Bombas de humo\n" +
            "🔫 Gancho\n" +
            "⚡ Tasers\n" +
            "🚓 Batimóvil\n" +
            "🛡 Armadura"

            );

        }

        function activarArmadura(){

            document.body.style.border =
            "8px solid cyan";

            document.getElementById("estado").innerHTML =
            "🛡 Armadura activada";

        }

        function usarBatarang(){

            puntos++;

            document.getElementById("puntos").innerHTML =
            puntos;

            document.getElementById("mensaje").innerHTML =
            "🦇 Batarang lanzado";

        }

        // BOSS

        function villanoFinal(){

            let juego =
            document.getElementById("juego");

            let boss =
            document.createElement("div");

            boss.classList.add("criminal");

            boss.innerHTML = "🃏";

            boss.style.width = "120px";
            boss.style.height = "120px";

            boss.style.fontSize = "60px";

            boss.style.background = "purple";

            boss.style.left = "40%";
            boss.style.top = "80px";

            boss.onclick = function(){

                puntos += 5;

                document.getElementById("puntos").innerHTML =
                puntos;

                document.getElementById("mensaje").innerHTML =
                "🏆 Joker derrotado";

                boss.remove();

            }

            juego.appendChild(boss);

        }

        // ENERGIA

        function recargar(){

            energia = 100;

            document.getElementById("energia").innerHTML =
            energia;

            document.getElementById("mensaje").innerHTML =
            "⚡ Energía restaurada";

        }

        // RELOJ

        function actualizarReloj(){

            let fecha =
            new Date();

            let hora =
            fecha.toLocaleTimeString();

            document.getElementById("reloj").innerHTML =
            "🕒 " + hora;

        }

        setInterval(actualizarReloj,1000);

    </script>

</body>

</html>function abrirArsenal(){

    let opcion = prompt(

    "🦾 ARSENAL BATMAN\n\n" +

    "1 = Batarang\n" +
    "2 = Bomba de humo\n" +
    "3 = Gancho\n" +
    "4 = Taser\n" +
    "5 = Batimóvil"

    );



    if(opcion == 1){

        document.getElementById("mensaje").innerHTML =
        "🦇 Batarang equipado";

        puntos++;

    }



    else if(opcion == 2){

        document.getElementById("mensaje").innerHTML =
        "💨function activarBatmovil(){

    document.getElementById("mensaje").innerHTML =
    "🏎 Batimóvil desplegado en Gotham";

    document.body.style.backgroundImage =
    "url('https://images.unsplash.com/photo-1500530855697-b586d89ba3ee?q=80&w=1400&auto=format&fit=crop')";

    energia -= 10;

    document.getElementById("energia").innerHTML =
    energia;

}function activarModoNoche(){

    document.body.style.filter =
    "brightness(60%)";

    document.getElementById("estado").innerHTML =
    "🌙 Modo sigilo activado";

}function activarModoNoche(){

    document.body.style.filter =
    "brightness(60%)";

    document.getElementById("estado").innerHTML =
    "🌙 Modo sigilo activado";

}function activarModoNoche(){

    document.body.style.filter =
    "brightness(60%)";

    document.getElementById("estado").innerHTML =
    "🌙 Modo sigilo activado";

}function llamarAlfred(){

    let frases = [

        "☕ Café preparado señor Wayne",
        "🛠 Batitraje reparado",
        "📡 Gotham monitoreada",
        "🦇 Todo está bajo control"

    ];

    let random =
    frases[Math.floor(Math.random()*frases.length)];

    document.getElementById("mensaje").innerHTML =
    random;

}function activarIA(){

    document.getElementById("estado").innerHTML =
    "🤖 IA JARVIS ACTIVADA";

    document.getElementById("juego").style.boxShadow =
    "0 0 30px cyan";

}function activarArmadura(){

    document.body.style.border =
    "8px solid cyan";

    document.getElementById("estado").innerHTML =
    "🛡 Armadura activada";

    energia += 20;

    if(energia > 100){

        energia = 100;

    }

    document.getElementById("energia").innerHTML =
    energia;

}function usarBatarang(){

    puntos++;

    document.getElementById("puntos").innerHTML =
    puntos;

    document.getElementById("mensaje").innerHTML =
    "🦇 Batarang lanzado";

}function recargar(){

    energia = 100;

    document.getElementById("energia").innerHTML =
    energia;

    document.getElementById("mensaje").innerHTML =
    "⚡ Energía restaurada";

}function llamarAlfred(){

    let opcion = prompt(

    "☕ ALFRED ONLINE\n\n" +

    "1 = Pedir café\n" +
    "2 = Estado de Gotham\n" +
    "3 = Reparar traje\n" +
    "4 = Consejo de Alfred"

    );



    if(opcion == 1){

        document.getElementById("mensaje").innerHTML =
        "☕ Alfred: Su café está listo señor Wayne";

    }



    else if(opcion == 2){

        document.getElementById("mensaje").innerHTML =
        "📡 Alfred: Gotham está bajo vigilancia";

    }



    else if(opcion == 3){

        energia = 100;

        document.getElementById("energia").innerHTML =
        energia;

        document.getElementById("mensaje").innerHTML =
        "🛠 Alfred reparó el Batitraje";

    }



    else if(opcion == 4){

        document.getElementById("mensaje").innerHTML =
        "🦇 Alfred: Incluso Batman necesita descansar";

    }



    else{

        document.getElementById("mensaje").innerHTML =
        "❌ Opción inválida";

    }

}<!-- AGREGA ESTE BOTÓN JUNTO A LOS DEMÁS -->

<button onclick="adivinarVillano()">
🎲 Juego secreto
</button>function adivinarVillano(){

    let villanos = [

        "joker",
        "bane",
        "riddler",
        "pinguino"

    ];

    let random =
    villanos[Math.floor(Math.random()*villanos.length)];



    let respuesta = prompt(

    "🎲 ADIVINA EL VILLANO\n\n" +

    "Opciones:\n" +
    "- joker\n" +
    "- bane\n" +
    "- riddler\n" +
    "- pinguino"

    );



    if(respuesta.toLowerCase() == random){

        puntos += 3;

        document.getElementById("puntos").innerHTML =
        puntos;

        document.getElementById("mensaje").innerHTML =
        "🏆 Correcto. Era " + random;

    }



    else{

        document.getElementById("mensaje").innerHTML =
        "❌ Incorrecto. Era " + random;

    }

}function adivinarVillano(){

    let villanos = [

        "joker",
        "bane",
        "riddler",
        "pinguino"

    ];

    let random =
    villanos[Math.floor(Math.random()*villanos.length)];



    let respuesta = prompt(

    "🎲 ADIVINA EL VILLANO\n\n" +

    "Opciones:\n" +
    "- joker\n" +
    "- bane\n" +
    "- riddler\n" +
    "- pinguino"

    );



    if(respuesta.toLowerCase() == random){

        puntos += 3;

        document.getElementById("puntos").innerHTML =
        puntos;

        document.getElementById("mensaje").innerHTML =
        "🏆 Correcto. Era " + random;

    }



    else{

        document.getElementById("mensaje").innerHTML =
        "❌ Incorrecto. Era " + random;

    }

}<!-- PEGA ESTO DEBAJO DEL DIV id="juego" -->

<div id="exhibicion"
style="
display:none;
margin-top:20px;
text-align:center;
">

<h2>🏛 BATCAVE EXHIBITION</h2>

<img
id="fotoBatman"
src="https://images.unsplash.com/photo-1511512578047-dfb367046420?q=80&w=1200&auto=format&fit=crop"
style="
width:300px;
border-radius:15px;
border:3px solid cyan;
box-shadow:0 0 20px cyan;
"
>

<p id="descripcionFoto"
style="
margin-top:15px;
font-size:22px;
color:lightgray;
">
Traje táctico de Batman
</p>

<br>

<button onclick="siguienteFoto()">
➡ Siguiente
</button>

<button onclick="cerrarExhibicion()">
❌ Cerrar
</button>

</div>let fotos = [

{
img:"https://images.unsplash.com/photo-1511512578047-dfb367046420?q=80&w=1200&auto=format&fit=crop",
texto:"🦇 Traje táctico de Batman"
},

{
img:"https://images.unsplash.com/photo-1500530855697-b586d89ba3ee?q=80&w=1200&auto=format&fit=crop",
texto:"🏎 Batimóvil desplegado"
},

{
img:"https://images.unsplash.com/photo-1519608487953-e999c86e7455?q=80&w=1200&auto=format&fit=crop",
texto:"🌃 Gotham City de noche"
}

];

let indiceFoto = 0;



function abrirExhibicion(){

    document.getElementById("exhibicion").style.display =
    "block";

    document.getElementById("mensaje").innerHTML =
    "🏛 Entrando a la sala de exhibición";

}



function siguienteFoto(){

    indiceFoto++;

    if(indiceFoto >= fotos.length){

        indiceFoto = 0;

    }

    document.getElementById("fotoBatman").src =
    fotos[indiceFoto].img;

    document.getElementById("descripcionFoto").innerHTML =
    fotos[indiceFoto].texto;

}



function cerrarExhibicion(){

    document.getElementById("exhibicion").style.display =
    "none";

    document.getElementById("mensaje").innerHTML =
    "🦇 Regresando a la Batcueva";

}<!-- PEGA ESTO DEBAJO DEL TITULO -->

<div id="batmanDialogo"
style="
display:flex;
align-items:center;
justify-content:center;
gap:20px;
margin-top:20px;
background:rgba(0,0,0,0.6);
padding:15px;
border-radius:20px;
border:2px solid cyan;
">

<img
id="batmanImg"
src="https://images.unsplash.com/photo-1511512578047-dfb367046420?q=80&w=1200&auto=format&fit=crop"

style="
width:180px;
height:180px;
object-fit:cover;
border-radius:20px;
border:3px solid cyan;
box-shadow:0 0 20px cyan;
"
>

<div>

<h2 style="color:cyan;">
🦇 Batman
</h2>

<p id="dialogoBatman"
style="
font-size:22px;
max-width:500px;
">
Gotham necesita un héroe.
</p>

</div>

</div><!-- AGREGA ESTOS BOTONES CON LOS DEMÁS -->

<button onclick="hablarBatman()">
💬 Hablar con Batman
</button>

<button onclick="modoDetective()">
🕵 Modo detective
</button>

<button onclick="peleaJoker()">
👊 Pelear con Joker
</button>function hablarBatman(){

    let frases = [

        "🦇 La noche es mi aliada.",
        "⚠ Gotham nunca duerme.",
        "👤 Un héroe actúa en silencio.",
        "🚓 Debemos proteger la ciudad.",
        "🃏 Joker está planeando algo."

    ];

    let random =
    frases[Math.floor(Math.random()*frases.length)];

    document.getElementById("dialogoBatman").innerHTML =
    random;

}function modoDetective(){

    let pista = prompt(

    "🕵 MODO DETECTIVE\n\n" +

    "Un criminal dejó una pista:\n" +

    "'Tengo alas pero no vuelo'\n\n" +

    "¿Quién soy?"

    );



    if(pista.toLowerCase() == "murcielago"){

        puntos += 5;

        document.getElementById("puntos").innerHTML =
        puntos;

        document.getElementById("dialogoBatman").innerHTML =
        "🦇 Correcto. Buen trabajo detective.";

        document.getElementById("mensaje").innerHTML =
        "🏆 Caso resuelto";

    }



    else{

        document.getElementById("dialogoBatman").innerHTML =
        "⚠ Esa no era la respuesta.";

        document.getElementById("mensaje").innerHTML =
        "❌ El criminal escapó";

    }

}function peleaJoker(){

    let ataque = prompt(

    "👊 PELEA CONTRA JOKER\n\n" +

    "1 = Golpe\n" +
    "2 = Batarang\n" +
    "3 = Esquivar"

    );



    let joker =
    Math.floor(Math.random()*3) + 1;



    if(ataque == joker){

        energia -= 20;

        document.getElementById("energia").innerHTML =
        energia;

        document.getElementById("dialogoBatman").innerHTML =
        "🃏 Joker te golpeó.";

        document.getElementById("mensaje").innerHTML =
        "💥 Ataque fallido";

    }



    else{

        puntos += 5;

        document.getElementById("puntos").innerHTML =
        puntos;

        document.getElementById("dialogoBatman").innerHTML =
        "🦇 Joker ha sido derrotado.";

        document.getElementById("mensaje").innerHTML =
        "🏆 Victoria";

    }

}<!-- BOTONES NUEVOS -->

<button onclick="abrirArcade()">
🕹 BAT-ARCADE
</button>

<button onclick="jugarCarrera()">
🏎 Carrera Batimóvil
</button>

<button onclick="jugarPuzzle()">
🧩 Puzzle Criminal
</button>

<button onclick="jugarRuleta()">
🎰 Ruleta Gotham
</button>

<button onclick="abrirMapa()">
🗺 Mapa Gotham
</button>

<button onclick="abrirBatcueva3D()">
🏛 Batcueva 3D
</button>/* FUNCIONES NUEVAS */


function abrirArcade(){

    document.getElementById("dialogoBatman").innerHTML =
    "🦇 Entrando al BAT-ARCADE";

    window.open(
    "https://poki.com",
    "_blank"
    );

}



function jugarCarrera(){

    document.getElementById("dialogoBatman").innerHTML =
    "🏎 Batimóvil preparado";

    window.open(
    "https://www.crazygames.com/t/car-games",
    "_blank"
    );

}



function jugarPuzzle(){

    let codigo =
    Math.floor(Math.random()*10);

    let respuesta = prompt(

    "🧩 DESACTIVA LA BOMBA\n\n" +

    "Adivina un número del 0 al 9"

    );



    if(respuesta == codigo){

        puntos += 10;

        document.getElementById("puntos").innerHTML =
        puntos;

        document.getElementById("mensaje").innerHTML =
        "🏆 Bomba desactivada";

        document.getElementById("dialogoBatman").innerHTML =
        "🦇 Excelente trabajo.";

    }



    else{

        energia -= 20;

        document.getElementById("energia").innerHTML =
        energia;

        document.getElementById("mensaje").innerHTML =
        "💥 La bomba explotó";

        document.getElementById("dialogoBatman").innerHTML =
        "⚠ Gotham sufrió daños.";

    }

}



function jugarRuleta(){

    let premio =
    Math.floor(Math.random()*4);



    if(premio == 0){

        puntos += 20;

        document.getElementById("mensaje").innerHTML =
        "💰 Ganaste puntos";

    }



    else if(premio == 1){

        energia += 20;

        if(energia > 100){

            energia = 100;

        }

        document.getElementById("mensaje").innerHTML =
        "⚡ Energía aumentada";

    }



    else if(premio == 2){

        document.getElementById("mensaje").innerHTML =
        "🃏 Joker robó tus monedas";

    }



    else{

        document.getElementById("mensaje").innerHTML =
        "🏆 Premio secreto desbloqueado";

    }



    document.getElementById("puntos").innerHTML =
    puntos;

    document.getElementById("energia").innerHTML =
    energia;

}



function abrirMapa(){

    document.getElementById("dialogoBatman").innerHTML =
    "🗺 Mostrando Gotham City";

    window.open(
    "https://www.google.com/maps",
    "_blank"
    );

}



function abrirBatcueva3D(){

    document.getElementById("dialogoBatman").innerHTML =
    "🏛 Explorando Batcueva";

    window.open(
    "https://sketchfab.com/search?q=batcave&type=models",
    "_blank"
    );

}
