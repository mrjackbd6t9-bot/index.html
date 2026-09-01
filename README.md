<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Football Team</title>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Arial, sans-serif;
}

body {
    background: #eef1f5;
    color: #222;
}

.header {
    background: #111827;
    color: white;
    text-align: center;
    padding: 25px 15px;
}

.header h1 {
    font-size: 28px;
    margin-bottom: 6px;
}

.header p {
    font-size: 14px;
    opacity: 0.8;
}

.container {
    width: 95%;
    max-width: 1100px;
    margin: 25px auto;
}

.search-box {
    margin-bottom: 25px;
}

.search-box input {
    width: 100%;
    padding: 15px 18px;
    border: 1px solid #ccc;
    border-radius: 12px;
    font-size: 16px;
    outline: none;
}

.search-box input:focus {
    border-color: #111827;
}

.players {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(230px, 1fr));
    gap: 20px;
}

.player-card {
    background: white;
    border-radius: 16px;
    padding: 20px;
    text-align: center;
    box-shadow: 0 5px 20px rgba(0,0,0,0.08);
}

.player-photo {
    width: 140px;
    height: 140px;
    border-radius: 50%;
    object-fit: cover;
    border: 4px solid #eee;
    margin-bottom: 12px;
}

.player-name {
    font-size: 21px;
    margin-bottom: 15px;
}

.info {
    text-align: left;
    border-top: 1px solid #eee;
    padding-top: 12px;
}

.info p {
    margin: 7px 0;
    font-size: 15px;
}

.info strong {
    display: inline-block;
    width: 90px;
}

.info a {
    color: #2563eb;
    text-decoration: none;
    font-weight: bold;
}

.not-found {
    display: none;
    text-align: center;
    margin-top: 30px;
    color: #777;
}

@media (max-width: 500px) {

    .header h1 {
        font-size: 24px;
    }

    .players {
        grid-template-columns: 1fr;
    }

    .player-card {
        max-width: 350px;
        width: 100%;
        margin: auto;
    }
}
</style>
</head>

<body>

<header class="header">
    <h1>⚽ Football Team</h1>
    <p>Total Players: 14</p>
</header>

<main class="container">

    <div class="search-box">
        <input
            type="text"
            id="searchInput"
            placeholder="🔎 Search player name..."
        >
    </div>

    <div class="players" id="playersContainer"></div>

    <div class="not-found" id="notFound">
        Player not found.
    </div>

</main>

<script>

const players = [

    {
        name: "Player 01",
        phone: "01700000001",
        jersey: "1",
        position: "Goalkeeper",
        photo: "images/player1.jpg"
    },

    {
        name: "Player 02",
        phone: "01700000002",
        jersey: "2",
        position: "Defender",
        photo: "images/player2.jpg"
    },

    {
        name: "Player 03",
        phone: "01700000003",
        jersey: "3",
        position: "Defender",
        photo: "images/player3.jpg"
    },

    {
        name: "Player 04",
        phone: "01700000004",
        jersey: "4",
        position: "Defender",
        photo: "images/player4.jpg"
    },

    {
        name: "Player 05",
        phone: "01700000005",
        jersey: "5",
        position: "Defender",
        photo: "images/player5.jpg"
    },

    {
        name: "Player 06",
        phone: "01700000006",
        jersey: "6",
        position: "Midfielder",
        photo: "images/player6.jpg"
    },

    {
        name: "Player 07",
        phone: "01700000007",
        jersey: "7",
        position: "Midfielder",
        photo: "images/player7.jpg"
    },

    {
        name: "Player 08",
        phone: "01700000008",
        jersey: "8",
        position: "Midfielder",
        photo: "images/player8.jpg"
    },

    {
        name: "Player 09",
        phone: "01700000009",
        jersey: "9",
        position: "Forward",
        photo: "images/player9.jpg"
    },

    {
        name: "Player 10",
        phone: "01700000010",
        jersey: "10",
        position: "Forward",
        photo: "images/player10.jpg"
    },

    {
        name: "Player 11",
        phone: "01700000011",
        jersey: "11",
        position: "Forward",
        photo: "images/player11.jpg"
    },

    {
        name: "Player 12",
        phone: "01700000012",
        jersey: "12",
        position: "Forward",
        photo: "images/player12.jpg"
    },

    {
        name: "Player 13",
        phone: "01700000013",
        jersey: "13",
        position: "Midfielder",
        photo: "images/player13.jpg"
    },

    {
        name: "Player 14",
        phone: "01700000014",
        jersey: "14",
        position: "Defender",
        photo: "images/player14.jpg"
    }

];


const playersContainer =
    document.getElementById("playersContainer");

const searchInput =
    document.getElementById("searchInput");

const notFound =
    document.getElementById("notFound");


function displayPlayers(playerList) {

    playersContainer.innerHTML = "";

    if (playerList.length === 0) {
        notFound.style.display = "block";
        return;
    }

    notFound.style.display = "none";

    playerList.forEach(player => {

        const card = document.createElement("div");

        card.className = "player-card";

        card.innerHTML = `

            <img
                class="player-photo"
                src="${player.photo}"
                alt="${player.name}"
            >

            <h2 class="player-name">
                ${player.name}
            </h2>

            <div class="info">

                <p>
                    <strong>📱 Phone:</strong>
                    <a href="tel:${player.phone}">
                        ${player.phone}
                    </a>
                </p>

                <p>
                    <strong>🔢 Jersey:</strong>
                    ${player.jersey}
                </p>

                <p>
                    <strong>⚽ Position:</strong>
                    ${player.position}
                </p>

            </div>
        `;

        playersContainer.appendChild(card);

    });
}


searchInput.addEventListener("input", function() {

    const searchText =
        this.value.toLowerCase().trim();

    const filteredPlayers =
        players.filter(player =>
            player.name.toLowerCase().includes(searchText)
        );

    displayPlayers(filteredPlayers);

});


displayPlayers(players);

</script>

</body>
</html>
