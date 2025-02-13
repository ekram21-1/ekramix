<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Valentine's Day ❤️</title>
    <style>
        /* Global Styles */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: 'Arial', sans-serif;
            background-color: #ffe6e6;
            color: #333;
            min-height: 100vh;
            overflow-x: hidden;
        }
        /* Floating Hearts */
        .heart {
            position: fixed;
            top: 100vh; /* Start off-screen at the bottom */
            left: calc(10% + 80% * var(--x-pos)); /* Randomized horizontal position */
            font-size: calc(10px + 20px * var(--size)); /* Randomized size */
            animation: floatHeart calc(3s + 2s * var(--speed)) linear infinite;
            opacity: calc(0.5 + 0.5 * var(--opacity)); /* Randomized opacity */
        }
        @keyframes floatHeart {
            0% {
                transform: translateY(0) translateX(0) rotate(0deg);
                opacity: 1;
            }
            50% {
                transform: translateY(-50vh) translateX(-10px) rotate(15deg);
            }
            100% {
                transform: translateY(-100vh) translateX(10px) rotate(-15deg);
                opacity: 0;
            }
        }
        /* Container */
        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 2rem;
        }
        header {
            text-align: center;
            padding: 2rem 0;
            animation: fadeIn 2s ease-in;
        }
        h1 {
            color: #ff4d4d;
            font-size: 3rem;
            margin-bottom: 1rem;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
        }
        /* Gallery */
        .gallery {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin: 2rem 0;
        }
        .gallery-item {
            background: white;
            padding: 1rem;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease;
            cursor: pointer;
        }
        .gallery-item:hover {
            transform: translateY(-5px);
        }
        .gallery-item img {
            width: 100%;
            height: 250px;
            object-fit: cover;
            border-radius: 5px;
            margin-bottom: 1rem;
        }
        /* Video Styling */
        .video-container video {
            border: 5px solid #fafafa;
            border-radius: 40px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        /* Valentine Card Styles */
        .valentine-card {
            width: 300px;
            height: 200px;
            margin: 2rem auto;
            perspective: 1500px;
            cursor: pointer;
        }
        .card {
            position: relative;
            width: 100%;
            height: 100%;
            transform-style: preserve-3d;
            transition: transform 1s;
        }
        .valentine-card.open .card {
            transform: rotateY(180deg);
        }
        .card-front, .card-back {
            position: absolute;
            width: 100%;
            height: 100%;
            backface-visibility: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        .card-front {
            background: #ff4d4d;
            color: white;
            font-size: 1.5rem;
        }
        .card-back {
            background: white;
            transform: rotateY(180deg);
            padding: 20px;
            text-align: center;
        }
        .envelope {
            font-size: 3rem;
            animation: pulse 2s infinite;
        }
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }
        /* Message */
        .message {
            background: white;
            padding: 2rem;
            border-radius: 10px;
            margin: 2rem 0;
            text-align: center;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        /* Controls */
        .controls {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: white;
            padding: 1rem;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            z-index: 1000;
        }
        button {
            background: #ff4d4d;
            color: white;
            border: none;
            padding: 0.5rem 1rem;
            border-radius: 5px;
            cursor: pointer;
            margin: 0.5rem;
            transition: background 0.3s ease;
        }
        button:hover {
            background: #ff3333;
        }
        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            z-index: 2000;
            justify-content: center;
            align-items: center;
        }
        .modal-content {
            max-width: 90%;
            max-height: 90vh;
        }
        .modal-content img {
            max-width: 100%;
            max-height: 90vh;
            object-fit: contain;
        }
        .close-modal {
            position: absolute;
            top: 20px;
            right: 20px;
            color: white;
            font-size: 2rem;
            cursor: pointer;
        }
        #musicControl {
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }
        .error-message {
            color: #ff4d4d;
            font-size: 0.8rem;
            margin-top: 0.5rem;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        /* Music Player Styles */
        .music-player {
            width: 250px; /* reduced width */
            background: white;
            border-radius: 10px;
            padding: 0.5rem; /* reduced padding */
        }

        .now-playing {
            text-align: center;
            margin-bottom: 0.5rem;
        }

        .song-title {
            font-size: 1rem;
            color: #333;
            margin: 0;
        }

        .artist-name {
            font-size: 0.8rem;
            color: #666;
            margin: 0.2rem 0 0 0;
        }

        .player-controls {
            display: flex;
            justify-content: center;
            gap: 0.5rem;
            margin-bottom: 0.5rem;
        }

        .control-button {
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            padding: 0.5rem;
            border-radius: 50%;
            transition: background-color 0.3s;
        }

        .control-button:hover {
            background: #f0f0f0;
        }

        .playlist-container {
            max-height: 200px;
            overflow-y: auto;
        }

        .playlist {
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
        }

        .playlist-item {
            padding: 0.5rem;
            background: #f8f8f8;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .playlist-item:hover {
            background: #f0f0f0;
        }

        .playlist-item.active {
            background: #ffe6e6;
            color: #ff4d4d;
        }

        /* Toggle Button Styles */
        .toggle-button {
            background: #ff4d4d;
            color: white;
            border: none;
            padding: 0.3rem 0.6rem;
            border-radius: 5px;
            cursor: pointer;
            margin-bottom: 0.5rem;
        }

        /* Utility class to hide elements */
        .hidden {
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Happy Valentine's Day!</h1>
        </header>
        <!-- Valentine Card -->
        <div class="valentine-card" onclick="toggleCard()">
            <div class="card">
                <div class="card-front">
                    <span class="envelope">✉️</span>
                </div>
                <div class="card-back">
                    <h2>Happy ❤️ Day</h2>
                </div>
            </div>
        </div>
        <div class="message">
            <p>
                From the moment I first saw you, I was captivated by your beauty. 
                But it's not just your outer beauty that draws me in – it's everything about you. 
                Your smile brightens even the darkest days, and your presence makes every moment more special.
                Meeting you has been one of the most wonderful things to happen in my life.
                You are truly beautiful, inside and out, and I feel blessed to have you in my life.
                This Valentine's Day, I simply want you to know how much you mean to me and how grateful I am that our paths crossed.
            </p>
        </div>
        <!-- Gallery -->
        <div class="gallery">
            <div class="gallery-item" onclick="openModal('m1.jpg', 'Our first date')">
                <img src="m1.jpg" alt="Our first date" loading="lazy" />
                <p></p>
            </div>
            <div class="gallery-item" onclick="openModal('m2.jpg', 'Our favorite place')">
                <img src="m2.jpg" alt="Our favorite place" loading="lazy" />
                <p></p>
            </div>
            <div class="gallery-item" onclick="openModal('m3.jpg', 'Special moment')">
                <img src="m3.jpg" alt="Special moment" loading="lazy" />
                <p></p>
            </div>
            <div class="gallery-item" onclick="openModal('m0.jpg', 'Special moment')">
                <img src="m0.jpg" alt="Special moment" loading="lazy" />
                <p></p>
            </div>
            <div class="gallery-item" onclick="openModal('m9.jpg', 'Special moment')">
                <img src="m9.jpg" alt="Special moment" loading="lazy" />
                <p></p>
            </div>
            <div class="gallery-item" onclick="openModal('m4.jpg', 'Together forever')">
                <img src="m4.jpg" alt="Together forever" loading="lazy" />
                <p></p>
            </div>
            <div class="gallery-item" onclick="openModal('m5.jpg', 'Together forever')">
                <img src="m5.jpg" alt="Together forever" loading="lazy" />
                <p></p>
            </div>
            <div class="gallery-item" onclick="openModal('m6.jpg', 'Together forever')">
                <img src="m6.jpg" alt="Together forever" loading="lazy" />
                <p></p>
            </div>
        </div>
        <div class="video-container" style="margin: 2rem auto; max-width: 400px;">
            <video width="100%" controls>
                <source src="vid1.mp4" type="video/mp4">
                Your browser does not support the video tag.
            </video>
        </div>
    </div>
    <!-- Music Player -->
    <div class="controls">
        <div class="music-player-container">
            <button id="toggleMusicPlayer" class="toggle-button">Show Music Player</button>
            <div id="music-player" class="music-player hidden">
                <div class="now-playing">
                    <h3 id="current-song-title" class="song-title">Select a song</h3>
                    <p id="current-artist" class="artist-name">-</p>
                </div>
                <div class="player-controls">
                    <button onclick="playPrevious()" class="control-button">⏮️</button>
                    <button onclick="togglePlay()" id="playPauseButton" class="control-button">▶️</button>
                    <button onclick="playNext()" class="control-button">⏭️</button>
                    <button onclick="toggleMute()" id="muteButton" class="control-button">🔊</button>
                </div>
                <div class="playlist-container">
                    <div id="playlist" class="playlist"></div>
                </div>
            </div>
        </div>
    </div>
    <!-- Modal for image preview -->
    <div class="modal" id="imageModal" onclick="closeModal()">
        <span class="close-modal">&times;</span>
        <div class="modal-content">
            <img id="modalImage" src="" alt="" />
        </div>
    </div>
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            console.log("DOM fully loaded - initializing scripts");
            // Updated Floating Hearts
            function createHeart() {
                const heart = document.createElement("div");
                heart.innerHTML = "❤️";
                heart.className = "heart";
                // Assign random values
                heart.style.setProperty("--x-pos", Math.random());
                heart.style.setProperty("--size", Math.random());
                heart.style.setProperty("--speed", Math.random());
                heart.style.setProperty("--opacity", Math.random());
                document.body.appendChild(heart);
                // Remove heart after animation completes
                setTimeout(() => heart.remove(), 5000);
            }
            // Create hearts at a random interval (every 200-400ms)
            setInterval(createHeart, 200 + Math.random() * 200);
            // Valentine Card Toggle
            window.toggleCard = function() {
                const card = document.querySelector('.valentine-card');
                card.classList.toggle('open');
            };
            // Music control
            window.audio = new Audio('romantic song.mp3'); // Update path if necessary.
            audio.loop = true;
            window.toggleMusic = function() {
                const musicButton = document.getElementById('musicButton');
                const musicStatus = document.getElementById('musicStatus');
                if (audio.paused) {
                    audio.play().catch(err => console.error("Error playing audio:", err));
                    musicStatus.textContent = '🎵';
                    musicButton.textContent = 'Pause Music';
                } else {
                    audio.pause();
                    musicStatus.textContent = '🔇';
                    musicButton.textContent = 'Play Music';
                }
            };
            // Modal functions for image preview
            window.openModal = function(imageSrc, altText) {
                const modal = document.getElementById('imageModal');
                const modalImg = document.getElementById('modalImage');
                modal.style.display = 'flex';
                modalImg.src = imageSrc;
                modalImg.alt = altText;
            };
            window.closeModal = function() {
                document.getElementById('imageModal').style.display = 'none';
            };
            // Close modal when pressing Escape key
            document.addEventListener('keydown', function(event) {
                if (event.key === 'Escape') closeModal();
            });
            // Prevent modal from closing when clicking on the image
            const modalContent = document.querySelector('.modal-content');
            if(modalContent) {
                modalContent.addEventListener('click', function(event) {
                    event.stopPropagation();
                });
            } else {
                console.warn("No .modal-content element found");
            }
            // Add fade-in animation to gallery items
            const galleryItems = document.querySelectorAll('.gallery-item');
            galleryItems.forEach((item, index) => {
                item.style.animation = `fadeIn 1s ease-in ${index * 0.2}s`;
            });
            // Preload images
            const images = ['m1.jpg', 'm2.jpg', 'm3.jpg', 'm4.jpg', 'm5.jpg', 'm6.jpg', 'm0.jpg', 'm9.jpg'];
            images.forEach(src => {
                const img = new Image();
                img.src = src;
            });
        });

        // Music Player Implementation
        const playlist = [
            { title: "Sa Bawat Sandali", artist: "Amiel Sol", file: "bawat.mp3" },
            { title: "Ikot", artist:" Over October",file: "over.mp3" },
            { title: "Grenade", artist: "Bruno Mars", file: "gre.mp3" },
            { title: "Just the Way You Are", artist: "Bruno Mars", file: "jt.mp3" },
            { title: "Your Gonna Live Forever in Me", artist: "John Mayer", file: "live.mp3" }, 
        ];

        let currentSongIndex = 0;
        let isPlaying = false;
        let currentAudio = new Audio(playlist[0].file);
        let nextAudio = new Audio();
        let fadeInterval;
        const fadeDuration = 1000; // 1 second fade

        // Initialize the playlist UI
        function initializePlaylist() {
            const playlistContainer = document.getElementById('playlist');
            playlist.forEach((song, index) => {
                const item = document.createElement('div');
                item.className = 'playlist-item' + (index === 0 ? ' active' : '');
                item.innerHTML = `
                    <div class="song-info">
                        <div class="song-title">${song.title}</div>
                        <div class="artist-name">${song.artist}</div>
                    </div>
                `;
                item.onclick = () => playSong(index);
                playlistContainer.appendChild(item);
            });
            updateNowPlaying();
        }

        // Update the Now Playing display
        function updateNowPlaying() {
            document.getElementById('current-song-title').textContent = playlist[currentSongIndex].title;
            document.getElementById('current-artist').textContent = playlist[currentSongIndex].artist;
            
            // Update active playlist item
            document.querySelectorAll('.playlist-item').forEach((item, index) => {
                item.className = 'playlist-item' + (index === currentSongIndex ? ' active' : '');
            });
        }

        // Fade audio
        function fadeAudio(audioElement, start, end, duration) {
            const interval = 50;
            const steps = duration / interval;
            const step = (end - start) / steps;
            
            clearInterval(fadeInterval);
            
            let currentVolume = start;
            fadeInterval = setInterval(() => {
                currentVolume = Math.min(1, Math.max(0, currentVolume + step));
                audioElement.volume = currentVolume;
                
                if ((step > 0 && currentVolume >= end) || (step < 0 && currentVolume <= end)) {
                    clearInterval(fadeInterval);
                    if (end === 0) {
                        audioElement.pause();
                    }
                }
            }, interval);
        }

        // Play a specific song
        async function playSong(index) {
            if (currentSongIndex === index && isPlaying) {
                return;
            }
            
            // Fade out current song
            if (isPlaying) {
                await new Promise(resolve => {
                    fadeAudio(currentAudio, currentAudio.volume, 0, fadeDuration);
                    setTimeout(resolve, fadeDuration);
                });
            }
            
            // Prepare next song
            currentSongIndex = index;
            nextAudio = new Audio(playlist[index].file);
            nextAudio.volume = 0;
            
            // Swap audio elements
            currentAudio.pause();
            currentAudio = nextAudio;
            
            // Play and fade in new song
            currentAudio.play();
            fadeAudio(currentAudio, 0, 1, fadeDuration);
            isPlaying = true;
            updatePlayButton();
            updateNowPlaying();
        }

        // Toggle play/pause
        function togglePlay() {
            if (isPlaying) {
                fadeAudio(currentAudio, currentAudio.volume, 0, fadeDuration);
                setTimeout(() => currentAudio.pause(), fadeDuration);
            } else {
                currentAudio.play();
                fadeAudio(currentAudio, 0, 1, fadeDuration);
            }
            isPlaying = !isPlaying;
            updatePlayButton();
        }

        // Update play/pause button
        function updatePlayButton() {
            document.getElementById('playPauseButton').textContent = isPlaying ? '⏸️' : '▶️';
        }

        // Play next song
        function playNext() {
            const nextIndex = (currentSongIndex + 1) % playlist.length;
            playSong(nextIndex);
        }

        // Play previous song
        function playPrevious() {
            const prevIndex = (currentSongIndex - 1 + playlist.length) % playlist.length;
            playSong(prevIndex);
        }

        // Toggle mute
        function toggleMute() {
            const muteButton = document.getElementById('muteButton');
            currentAudio.muted = !currentAudio.muted;
            muteButton.textContent = currentAudio.muted ? '🔇' : '🔊';
        }

        // Initialize when DOM is loaded
        document.addEventListener('DOMContentLoaded', function() {
            initializePlaylist();
            currentAudio.volume = 0;
        });

        // Handle song ending
        currentAudio.addEventListener('ended', playNext);

        // Toggle Music Player Visibility
        document.addEventListener('DOMContentLoaded', function() {
            const toggleButton = document.getElementById('toggleMusicPlayer');
            const musicPlayer = document.getElementById('music-player');

            toggleButton.addEventListener('click', function() {
                if (musicPlayer.classList.contains('hidden')) {
                    musicPlayer.classList.remove('hidden');
                    toggleButton.textContent = "Hide Music Player";
                } else {
                    musicPlayer.classList.add('hidden');
                    toggleButton.textContent = "Show Music Player";
                }
            });
        });
    </script>
</body>
</html>
