<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Minecraft Links</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            font-family: Arial, sans-serif;
            background-image: url('https://lowcygier.pl/wp-content/uploads/2024/05/minecraft-facebook-temp-720x378.jpg');
            background-size: cover;
            background-position: top;
            color: #000;
        }
        h1 {
            color: green;
            text-align: center;
            margin-top: 20px;
            font-size: 50px; /* Zwiekszony rozmiar napisu Minecraft */
        }
        .links {
            text-align: center;
            margin-top: 50px;
        }
        .links a {
            display: block;
            color: black;
            text-decoration: none;
            font-size: 30px; /* Zwiekszony rozmiar linków */
            margin: 15px 0;
        }
        .links a:hover {
            text-decoration: underline;
        }
        #context-menu {
            display: none;
            position: absolute;
            background-color: white;
            border: 1px solid #ccc;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
            z-index: 1000;
            font-size: 20px; /* Zwiekszony rozmiar tekstu w menu kontekstowym */
        }
        #context-menu ul {
            list-style: none;
            margin: 0;
            padding: 10px;
        }
        #context-menu ul li {
            padding: 10px 20px;
            cursor: pointer;
        }
        #context-menu ul li:hover {
            background-color: #f0f0f0;
        }
        #settings-button {
            position: fixed;
            top: 10px;
            right: 10px;
            width: 60px;
            height: 60px;
            background-image: url('https://cdn.pixabay.com/photo/2015/07/23/13/08/gear-856921_1280.png');
            background-size: 50px 50px; /* Zwiekszona ikona ustawien */
            background-color: transparent;
            border: none;
            cursor: pointer;
        }
        #language-menu {
            display: none;
            position: fixed;
            top: 60px;
            right: 10px;
            background-color: white;
            border: 1px solid #ccc;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
            z-index: 1000;
            font-size: 20px; /* Zwiekszony rozmiar tekstu w menu jezykowym */
        }
        #language-menu ul {
            list-style: none;
            margin: 0;
            padding: 10px;
        }
        #language-menu ul li {
            padding: 10px 20px;
            cursor: pointer;
        }
        #language-menu ul li:hover {
            background-color: #f0f0f0;
        }
        #notepad-button {
            position: fixed;
            bottom: 60px;
            right: 10px;
            width: 60px;
            height: 60px;
            background-image: url('https://icons-for-free.com/iff/png/512/notepad-131994967967763378.png');
            background-size: 50px 50px; /* Zwiekszona ikona notatnika */
            background-color: transparent;
            border: none;
            cursor: pointer;
        }
        #notepad {
            display: none;
            position: fixed;
            bottom: 110px;
            right: 10px;
            width: 350px;
            height: 250px;
            background-color: white;
            border: 1px solid #ccc;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
            padding: 15px;
            overflow-y: auto;
            z-index: 1000;
            font-size: 18px; /* Zwiekszony rozmiar tekstu w notatniku */
        }
        .footer {
            position: absolute;
            top: 10px;
            left: 10px;
            font-size: 18px; /* Zwiekszony rozmiar tekstu w stopce */
        }
        .footer a {
            color: blue;
            text-decoration: none;
        }
        .footer a:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <h1 id="title">Minecraft</h1>

    <div class="links">
        <a href="https://eaglercraft.com/mc/1.8.8/" target="_blank" id="link-1">1.8.8</a>
        <a href="https://eaglercraft.com/mc/scratch/" target="_blank" id="link-2">scratch</a>
    </div>

    <div id="context-menu">
        <ul>
            <li onclick="goToServers()" id="context-servers">Serwery</li>
            <li onclick="goToCommands()" id="context-commands">Komendy</li>
            <li onclick="goToTextures()" id="context-textures">Texturki</li>
        </ul>
    </div>

    <button id="settings-button"></button>

    <button id="notepad-button"></button>

    <div id="notepad">
        <h3 id="notepad-title">Ciekawe Seedy</h3>
        <p><strong id="version-1-8-8">1.8.8:</strong></p>
        <ul id="seeds-1-8-8">
            <li>Seed 1: 123456789</li>
            <li>Seed 2: 987654321</li>
            <li>Seed 3: 456123789</li>
        </ul>
        <p><strong id="version-scratch">Scratch Edition:</strong></p>
        <ul id="seeds-scratch">
            <li>Seed A: abc123</li>
            <li>Seed B: xyz789</li>
            <li>Seed C: minecraft2024</li>
        </ul>
    </div>

    <div id="language-menu">
        <ul>
            <li onclick="setLanguage('pl')">Polski (PL)</li>
            <li onclick="setLanguage('en')">Angielski (ANG)</li>
            <li onclick="setLanguage('de')">Niemiecki (DEU)</li>
        </ul>
    </div>

    <div class="footer">
        <span id="footer-text">Stworzone przez Noah Kieda. Minecraft wyprodukowany przez <a href="https://eaglercraft.com/" target="_blank" id="eaglecraft-link">Eaglecraft</a>.</span>
    </div>

    <script>
        const contextMenu = document.getElementById('context-menu');
        const languageMenu = document.getElementById('language-menu');
        const settingsButton = document.getElementById('settings-button');
        const notepadButton = document.getElementById('notepad-button');
        const notepad = document.getElementById('notepad');

        document.addEventListener('contextmenu', function (e) {
            e.preventDefault();
            contextMenu.style.top = `${e.pageY}px`;
            contextMenu.style.left = `${e.pageX}px`;
            contextMenu.style.display = 'block';
        });

        document.addEventListener('click', function () {
            contextMenu.style.display = 'none';
            languageMenu.style.display = 'none';
            notepad.style.display = 'none';
        });

        settingsButton.addEventListener('click', function (e) {
            e.stopPropagation();
            languageMenu.style.display = languageMenu.style.display === 'block' ? 'none' : 'block';
        });

        notepadButton.addEventListener('click', function (e) {
            e.stopPropagation();
            notepad.style.display = notepad.style.display === 'block' ? 'none' : 'block';
        });

        function goToServers() {
            window.open('https://servers.eaglercraft.com/', '_blank');
        }

        function goToCommands() {
            window.open('https://www.gamergeeks.net/', '_blank');
        }

        function goToTextures() {
            window.open('https://resourcepack.net/res/minecraft-1-8-8-resource-packs/page/3/#gsc.tab=0', '_blank');
        }

        function setLanguage(lang) {
            const translations = {
                pl: {
                    title: 'Minecraft',
                    links: ['1.8.8', 'scratch'],
                    contextMenu: ['Serwery', 'Komendy', 'Texturki'],
                    notepadTitle: 'Ciekawe Seedy',
                    version1_8_8: '1.8.8:',
                    seeds1_8_8: ['Seed 1: 123456789', 'Seed 2: 987654321', 'Seed 3: 456123789'],
                    versionScratch: 'Scratch Edition:',
                    seedsScratch: ['Seed A: abc123', 'Seed B: xyz789', 'Seed C: minecraft2024'],
                    footerText: 'Stworzone przez Noah Kieda. Minecraft wyprodukowany przez Eaglecraft.',
                    eaglecraftLink: 'https://eaglercraft.com/'
                },
                en: {
                    title: 'Minecraft',
                    links: ['1.8.8', 'scratch'],
                    contextMenu: ['Servers', 'Commands', 'Textures'],
                    notepadTitle: 'Interesting Seeds',
                    version1_8_8: '1.8.8:',
                    seeds1_8_8: ['Seed 1: 123456789', 'Seed 2: 987654321', 'Seed 3: 456123789'],
                    versionScratch: 'Scratch Edition:',
                    seedsScratch: ['Seed A: abc123', 'Seed B: xyz789', 'Seed C: minecraft2024'],
                    footerText: 'Created by Noah Kieda. Minecraft produced by Eaglecraft.',
                    eaglecraftLink: 'https://eaglercraft.com/'
                },
                de: {
                    title: 'Minecraft',
                    links: ['1.8.8', 'scratch'],
                    contextMenu: ['Server', 'Befehle', 'Texturen'],
                    notepadTitle: 'Interessante Seeds',
                    version1_8_8: '1.8.8:',
                    seeds1_8_8: ['Seed 1: 123456789', 'Seed 2: 987654321', 'Seed 3: 456123789'],
                    versionScratch: 'Scratch Edition:',
                    seedsScratch: ['Seed A: abc123', 'Seed B: xyz789', 'Seed C: minecraft2024'],
                    footerText: 'Erstellt von Noah Kieda. Minecraft produziert von Eaglecraft.',
                    eaglecraftLink: 'https://eaglercraft.com/'
                }
            };

            const translation = translations[lang];

            document.getElementById('title').textContent = translation.title;
            document.getElementById('link-1').textContent = translation.links[0];
            document.getElementById('link-2').textContent = translation.links[1];
            document.getElementById('context-servers').textContent = translation.contextMenu[0];
            document.getElementById('context-commands').textContent = translation.contextMenu[1];
            document.getElementById('context-textures').textContent = translation.contextMenu[2];
            document.getElementById('notepad-title').textContent = translation.notepadTitle;
            document.getElementById('version-1-8-8').textContent = translation.version1_8_8;
            document.getElementById('version-scratch').textContent = translation.versionScratch;
            document.getElementById('footer-text').innerHTML = `${translation.footerText} Minecraft produced by <a href="${translation.eaglecraftLink}" target="_blank" id="eaglecraft-link">Eaglecraft</a>.`;

            const seeds1_8_8 = document.getElementById('seeds-1-8-8');
            const seedsScratch = document.getElementById('seeds-scratch');

            seeds1_8_8.innerHTML = '';
            seedsScratch.innerHTML = '';

            translation.seeds1_8_8.forEach(seed => {
                const li = document.createElement('li');
                li.textContent = seed;
                seeds1_8_8.appendChild(li);
            });

            translation.seedsScratch.forEach(seed => {
                const li = document.createElement('li');
                li.textContent = seed;
                seedsScratch.appendChild(li);
            });
        }
    </script>
</body>
</html>

