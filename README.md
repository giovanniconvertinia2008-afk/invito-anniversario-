<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>50° Anniversario di Matrimonio</title>
    <style>
        /* BODY E SFONDO */
        body {
            margin: 0;
            font-family: 'Georgia', serif;
            background: url('https://www.dropbox.com/scl/fi/geh3jcyjhieei45kd2pb1/nonni.jpeg?rlkey=9532cve97cg4b8ave3pxcau5e&raw=1') no-repeat center center fixed;
            background-size: cover;
            color: #ffffff;
        }

        /* OVERLAY SCURO PER LEGGIBILITÀ */
        .overlay {
            background-color: rgba(0, 0, 0, 0.55);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
            box-sizing: border-box;
        }

        /* CONTAINER INVITO */
        .invito {
            background: rgba(255, 255, 255, 0.12);
            border: 2px solid #d4af37;
            padding: 30px 20px;
            text-align: center;
            max-width: 500px;
            width: 100%;
            border-radius: 15px;
        }

        /* TITOLI */
        h1 {
            color: #d4af37;
            font-size: 2.5rem;
            margin-bottom: 10px;
        }

        h2 {
            font-weight: normal;
            font-size: 1.5rem;
            margin-bottom: 20px;
        }

        /* PARAGRAFI E INFO */
        p {
            font-size: 1rem;
            line-height: 1.6;
            margin-bottom: 20px;
        }

        .info {
            font-size: 1.1rem;
            margin-bottom: 20px;
        }

        a.location {
            display: inline-block;
            margin-bottom: 20px;
            color: #d4af37;
            text-decoration: none;
            font-weight: bold;
            word-break: break-word;
        }

        /* INPUT NOME */
        input[type="text"] {
            padding: 12px;
            font-size: 1rem;
            border-radius: 8px;
            border: 1px solid #d4af37;
            margin: 10px 0;
            width: 90%;
            max-width: 300px;
            box-sizing: border-box;
        }

        /* PULSANTI */
        .risposte button {
            padding: 12px 25px;
            margin: 10px 5px;
            font-size: 1rem;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            width: 45%;
            max-width: 200px;
        }

        .si {
            background-color: #d4af37;
            color: #000;
        }

        .no {
            background-color: #ffffff;
            color: #000;
        }

        button:hover {
            opacity: 0.85;
        }

        /* RESPONSIVE TEXT */
        @media (max-width: 600px) {
            h1 { font-size: 2rem; }
            h2 { font-size: 1.2rem; }
            p, .info { font-size: 0.95rem; }
            input[type="text"] { font-size: 0.95rem; }
            .risposte button { font-size: 0.95rem; padding: 10px; width: 100%; max-width: none; }
        }
    </style>
</head>
<body>

<div class="overlay">
    <div class="invito">
        <h1>50° Anniversario<br>
            di matrimonio</h1>

        <p>
            "Ciō che Dio ha unito<br> 
            l'uomo non separi"<br>
            -Matteo 19:6-<br>             
            Con immensa gioia<br>
            vi invitiamo a celebrare con noi<br>
            un traguardo d’amore senza tempo
        </p>

        <div class="info">
            📍 <strong>Villa Bonfrate</strong><br>
            Leporano (Taranto)<br><br>
            🗓 <strong>21 Febbraio 2026</strong><br>
            🕢 <strong>Ore 19:30</strong>
        </div>

        <a class="location" href="https://www.google.com/maps/place/Villa+Bonfrate/@40.3730649,17.3135458,17z/data=!4m6!3m5!1s0x1346e3b455555555:0xbca25e85bf960151!8m2!3d40.3736371!4d17.3130523!16s%2Fg%2F11df0n1sg2?entry=ttu&g_ep=EgoyMDI2MDExMy4wIKXMDSoASAFQAw%3D%3D" target="_blank">
            📌 Vedi la posizione della Villa
        </a>

        <!-- INPUT NOME -->
        <div>
            <input type="text" id="nome" placeholder="Inserisci il tuo nome">
        </div>

        <!-- PULSANTI SÌ/NO -->
        <div class="risposte">
            <button class="si" onclick="inviaRisposta('SI')">✔️ Parteciperò</button>
            <button class="no" onclick="inviaRisposta('NO')">❌ Non potrò partecipare</button>
        </div>
    </div>
</div>

<script>
function inviaRisposta(risposta) {
    const nome = document.getElementById("nome").value.trim();

    if(nome === "") {
        alert("Per favore, inserisci il tuo nome!");
        return;
    }

    // METTI QUI IL TOKEN E CHAT ID CORRETTI
    const token = "8552836610:AAH55wROSVtQQz5B776TPaCdKCNAlEPaNSg";
    const chatId = "5893616862";

    const messaggio = encodeURIComponent(
        `💍 50° Anniversario di Matrimonio\n` +
        `📍 Villa Bonfrate – Leporano (TA)\n` +
        `🗓 21 Febbraio 2026 – Ore 19:30\n\n` +
        `Nome invitato: ${nome}\n` +
        `Risposta: ${risposta}`
    );

    const url = `https://api.telegram.org/bot${token}/sendMessage?chat_id=${chatId}&text=${messaggio}`;

    fetch(url)
        .then(response => {
            if(response.ok){
                alert("Grazie per la tua risposta 💛");
                document.getElementById("nome").value = "";
            } else {
                alert("Errore nell'invio, riprova.");
                console.error(response);
            }
        })
        .catch(error => {
            alert("Errore nella connessione, riprova.");
            console.error(error);
        });
}
</script>

</body>
</html>
