.p2-border { border-color: #f97316; }
        .btn-bounce:active { transform: scale(0.95); }
        
        @keyframes pulse-shake {
            0%, 100% { transform: translateX(0); }
            20%, 60% { transform: translateX(-8px) rotate(-2deg); }
            40%, 80% { transform: translateX(8px) rotate(2deg); }
        }
        .animate-shake { animation: pulse-shake 0.4s ease-in-out<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tebak Jokes Bapak-Bapak Duo - Kuis Receh 2 Pemain</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;600;700&family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #080c14;
            color: #f8fafc;
            user-select: none;
        }
        .font-game {
            font-family: 'Fredoka', cursive;
        }
        .glass-card {
            background: rgba(15, 23, 42, 0.82);
            backdrop-filter: blur(16px);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        .p1-gradient {
            background: linear-gradient(135deg, #3b82f6 0%, #1d4ed8 100%);
        }
        .p2-gradient {
            background: linear-gradient(135deg, #f97316 0%, #c2410c 100%);
        }
        .p1-border { border-color: #3b82f6; }; }

        @keyframes pop-bounce {
            0% { transform: scale(0.5); opacity: 0; }
            70% { transform: scale(1.1); opacity: 1; }
            100% { transform: scale(1); opacity: 1; }
        }
        .animate-pop { animation: pop-bounce 0.35s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards; }
        
        @keyframes float-up {
            0% { opacity: 1; transform: translateY(0) scale(1); }
            100% { opacity: 0; transform: translateY(-40px) scale(1.2); }
        }
        .animate-float { animation: float-up 0.8s ease-out forwards; }
    </style>
</head>
<body class="min-h-screen flex flex-col justify-between items-center p-3 sm:p-5 overflow-x-hidden">

    <header class="w-full max-w-4xl glass-card rounded-2xl p-3.5 sm:p-4 mb-3 flex justify-between items-center shadow-2xl border border-slate-800">
        <div class="flex items-center gap-3">
            <div class="w-10 h-10 sm:w-12 sm:h-12 rounded-2xl bg-gradient-to-tr from-amber-500 via-orange-500 to-yellow-400 flex items-center justify-center text-2xl text-white font-bold shadow-lg shadow-orange-950/50">
                ☕
            </div>
            <div>
                <h1 class="font-game text-xl sm:text-2xl font-bold tracking-wide text-transparent bg-clip-text bg-gradient-to-r from-yellow-300 via-orange-400 to-amber-200">
                    TEBAK JOKES BAPAK-BAPAK DUO
                </h1>
                <p class="text-[11px] sm:text-xs text-slate-400">Pass & Play 2 Pemain • Paling Receh & Bikin Ngakak!</p>
            </div>
        </div>

        <div class="flex items-center gap-2">
            <button onclick="toggleSound()" id="soundBtn" class="p-2.5 rounded-xl bg-slate-800 hover:bg-slate-700 text-slate-300 transition border border-slate-700" title="Suara On/Off">
                <i class="fa-solid fa-volume-high text-sm"></i>
            </button>
            <button onclick="resetToMenu()" class="p-2.5 rounded-xl bg-slate-800 hover:bg-slate-700 text-slate-300 transition border border-slate-700 text-xs font-semibold flex items-center gap-1.5">
                <i class="fa-solid fa-house text-sm"></i> <span class="hidden sm:inline">Menu Utama</span>
            </button>
        </div>
    </header>

    <main class="w-full max-w-4xl flex-1 flex flex-col items-center justify-center relative">

        <!-- Floating Reaction Container -->
        <div id="floatingReactionBox" class="pointer-events-none absolute inset-0 z-50 flex items-center justify-center overflow-hidden"></div>

        <!-- SCREEN 1: MENU UTAMA -->
        <section id="menuScreen" class="w-full max-w-2xl glass-card rounded-3xl p-6 sm:p-8 flex flex-col gap-6 shadow-2xl border border-slate-800">
            <div class="text-center space-y-2">
                <span class="px-3.5 py-1 rounded-full bg-amber-950/80 text-amber-400 text-xs font-bold border border-amber-800/80 inline-flex items-center gap-1.5 shadow-md">
                    <span>☕</span> Kuis Humor Receh & Paling Absurd
                </span>
                <h2 class="font-game text-4xl sm:text-5xl font-bold text-slate-100 tracking-tight">
                    ARENA JOKES RECEH
                </h2>
                <p class="text-xs sm:text-sm text-slate-400 max-w-md mx-auto">
                    Uji seberapa tahan kamu menahan tawa (atau sakit kepala) dari tebak-tebakan garing bapak-bapak!
                </p>
            </div>

            <!-- Input Nama Pemain -->
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                <div class="bg-slate-900/90 p-4 rounded-2xl border border-blue-500/40 space-y-2 shadow-inner">
                    <label class="text-xs font-bold text-blue-400 flex items-center gap-1.5 uppercase">
                        <i class="fa-solid fa-user-gear"></i> Pemain 1 (Biru)
                    </label>
                    <input type="text" id="p1NameInput" value="Bapak Agus" class="w-full bg-slate-800/90 border border-slate-700 rounded-xl px-3.5 py-2.5 text-sm text-white focus:outline-none focus:border-blue-400 font-semibold" placeholder="Nama Pemain 1">
                </div>

                <div class="bg-slate-900/90 p-4 rounded-2xl border border-orange-500/40 space-y-2 shadow-inner">
                    <label class="text-xs font-bold text-orange-400 flex items-center gap-1.5 uppercase">
                        <i class="fa-solid fa-user-gear"></i> Pemain 2 (Jingga)
                    </label>
                    <input type="text" id="p2NameInput" value="Bapak Bambang" class="w-full bg-slate-800/90 border border-slate-700 rounded-xl px-3.5 py-2.5 text-sm text-white focus:outline-none focus:border-orange-400 font-semibold" placeholder="Nama Pemain 2">
                </div>
            </div>

            <!-- Pilih Kategori -->
            <div class="space-y-2.5">
                <div class="flex justify-between items-center">
                    <label class="text-xs font-bold text-slate-300 block uppercase tracking-wider">Kategori Jokes</label>
                    <span class="text-[10px] text-amber-400 font-semibold">Semua bikin ngakak!</span>
                </div>
                <div class="grid grid-cols-2 sm:grid-cols-3 gap-2.5">
                    <button onclick="selectCategory('all')" id="cat-all" class="cat-btn bg-amber-600 border-2 border-amber-400 text-white p-3 rounded-2xl text-xs font-bold transition flex flex-col items-center gap-1.5 shadow-lg">
                        <span class="text-2xl">🌟</span> Campur Aduk (Semua)
                    </button>
                    <button onclick="selectCategory('plesetan')" id="cat-plesetan" class="cat-btn bg-slate-800/80 border border-slate-700 hover:border-slate-500 text-slate-300 p-3 rounded-2xl text-xs font-bold transition flex flex-col items-center gap-1.5">
                        <span class="text-2xl">☕</span> Plesetan Kata
                    </button>
                    <button onclick="selectCategory('hewan')" id="cat-hewan" class="cat-btn bg-slate-800/80 border border-slate-700 hover:border-slate-500 text-slate-300 p-3 rounded-2xl text-xs font-bold transition flex flex-col items-center gap-1.5">
                        <span class="text-2xl">🦎</span> Hewan Receh
                    </button>
                    <button onclick="selectCategory('makanan')" id="cat-makanan" class="cat-btn bg-slate-800/80 border border-slate-700 hover:border-slate-500 text-slate-300 p-3 rounded-2xl text-xs font-bold transition flex flex-col items-center gap-1.5">
                        <span class="text-2xl">🥕</span> Makanan & Sayur
                    </button>
                    <button onclick="selectCategory('sehari')" id="cat-sehari" class="cat-btn bg-slate-800/80 border border-slate-700 hover:border-slate-500 text-slate-300 p-3 rounded-2xl text-xs font-bold transition flex flex-col items-center gap-1.5">
                        <span class="text-2xl">🚗</span> Kehidupan Bapak
                    </button>
                    <button onclick="selectCategory('pop')" id="cat-pop" class="cat-btn bg-slate-800/80 border border-slate-700 hover:border-slate-500 text-slate-300 p-3 rounded-2xl text-xs font-bold transition flex flex-col items-center gap-1.5">
                        <span class="text-2xl">🎬</span> Pop & Musik Receh
                    </button>
                </div>
            </div>

            <!-- Jumlah Ronde -->
            <div class="space-y-1.5">
                <label class="text-xs font-bold text-slate-300 block uppercase tracking-wider">JUMLAH RONDE PERMAINAN</label>
                <select id="questionCountSelect" class="w-full bg-slate-900 border border-slate-700 rounded-xl px-3.5 py-3 text-xs font-semibold text-slate-200 focus:outline-none focus:border-amber-400">
                    <option value="5">5 Ronde (Kuis Singkat)</option>
                    <option value="10" selected>10 Ronde (Standar Kopi Hitam)</option>
                    <option value="15">15 Ronde (Maraton Ketawa)</option>
                    <option value="20">20 Ronde (Receh Maksimal)</option>
                </select>
            </div>

            <button onclick="startGame()" class="btn-bounce w-full py-4 rounded-2xl bg-gradient-to-r from-amber-500 via-orange-500 to-yellow-500 hover:opacity-95 text-slate-950 font-game text-2xl font-bold tracking-wide shadow-xl shadow-orange-950/50 transition flex items-center justify-center gap-2">
                <span>🚀</span> MULAI PERTANDINGAN RECEH
            </button>
        </section>

        <!-- SCREEN 2: GAMEPLAY -->
        <section id="gameScreen" class="hidden w-full flex flex-col gap-3.5">

            <!-- Papan Skor Dua Pemain -->
            <div class="grid grid-cols-2 gap-3 sm:gap-4">
                <!-- Status Pemain 1 -->
                <div id="p1Card" class="glass-card p-3.5 sm:p-4 rounded-2xl border-2 p1-border flex items-center justify-between transition-all">
                    <div>
                        <span class="text-[11px] font-bold text-blue-400 block uppercase tracking-wider" id="p1NameLabel">PEMAIN 1</span>
                        <div class="flex items-baseline gap-1.5 mt-0.5">
                            <span id="p1Score" class="font-game text-3xl sm:text-4xl font-bold text-white">0</span>
                            <span class="text-[10px] text-slate-400">Poin</span>
                        </div>
                    </div>
                    <div id="p1Badge" class="w-10 h-10 rounded-xl p1-gradient flex items-center justify-center font-bold text-white shadow-md text-sm">
                        P1
                    </div>
                </div>

                <!-- Status Pemain 2 -->
                <div id="p2Card" class="glass-card p-3.5 sm:p-4 rounded-2xl border-2 border-transparent flex items-center justify-between transition-all">
                    <div id="p2Badge" class="w-10 h-10 rounded-xl bg-slate-800 flex items-center justify-center font-bold text-slate-400 shadow-md text-sm">
                        P2
                    </div>
                    <div class="text-right">
                        <span class="text-[11px] font-bold text-orange-400 block uppercase tracking-wider" id="p2NameLabel">PEMAIN 2</span>
                        <div class="flex items-baseline justify-end gap-1.5 mt-0.5">
                            <span id="p2Score" class="font-game text-3xl sm:text-4xl font-bold text-white">0</span>
                            <span class="text-[10px] text-slate-400">Poin</span>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Banner Turn & Status -->
            <div class="glass-card p-3 rounded-2xl border border-slate-800 flex justify-between items-center text-xs flex-wrap gap-2">
                <div class="flex items-center gap-2">
                    <span id="turnIndicator" class="px-3 py-1.5 rounded-full font-bold p1-gradient text-white shadow-md text-xs">
                        🎯 GILIRAN: PEMAIN 1
                    </span>
                    <span id="stealBadge" class="hidden px-2.5 py-1 rounded-md bg-orange-950 text-orange-300 border border-orange-700 text-[10px] font-bold animate-pulse">
                        ⚡ REBUT POIN (+5 BONUS)!
                    </span>
                </div>

                <div class="flex items-center gap-2.5 text-[11px]">
                    <span id="questionTracker" class="font-semibold text-slate-300 bg-slate-900 px-2.5 py-1 rounded-lg border border-slate-800">Ronde 1 / 10</span>
                    <span id="rewardPointsBadge" class="px-2.5 py-1 rounded-lg bg-emerald-950 text-emerald-400 border border-emerald-800 font-mono font-bold">
                        💎 Nilai: 30 Poin
                    </span>
                </div>
            </div>

            <!-- Sound Reaction Taunt Bar -->
            <div class="glass-card px-3 py-2 rounded-xl border border-slate-800 flex items-center justify-between gap-2">
                <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider flex items-center gap-1">
                    <i class="fa-solid fa-face-laugh-beam text-amber-400"></i> Tombol Ejekan:
                </span>
                <div class="flex items-center gap-1.5">
                    <button onclick="triggerTaunt('drum')" class="btn-bounce px-2.5 py-1 rounded-lg bg-slate-800 hover:bg-slate-700 text-[11px] font-bold text-amber-300 border border-slate-700">
                        🥁 Drumroll
                    </button>
                    <button onclick="triggerTaunt('laugh')" class="btn-bounce px-2.5 py-1 rounded-lg bg-slate-800 hover:bg-slate-700 text-[11px] font-bold text-yellow-300 border border-slate-700">
                        😂 Wkwkwk
                    </button>
                    <button onclick="triggerTaunt('facepalm')" class="btn-bounce px-2.5 py-1 rounded-lg bg-slate-800 hover:bg-slate-700 text-[11px] font-bold text-rose-300 border border-slate-700">
                        🤦 Facepalm
                    </button>
                </div>
            </div>

            <!-- Kotak Misteri Jokes -->
            <div class="glass-card p-5 sm:p-7 rounded-3xl border border-slate-800 shadow-2xl space-y-5 relative">
                
                <div class="flex justify-between items-center border-b border-slate-800/80 pb-3">
                    <span id="categoryBadge" class="text-[11px] uppercase tracking-wider font-bold text-amber-400 bg-amber-950/80 px-3 py-1 rounded-lg border border-amber-800">
                        ☕ PLESETAN KATA
                    </span>
                    <button onclick="revealNextClue()" id="revealClueBtn" class="text-xs text-amber-300 hover:text-amber-200 font-bold flex items-center gap-1.5 bg-amber-950/60 px-3.5 py-1.5 rounded-xl border border-amber-800/60 shadow transition">
                        <i class="fa-solid fa-lightbulb"></i> Buka Petunjuk Ke-<span id="nextClueNum">2</span> (-10 Poin)
                    </button>
                </div>

                <!-- Clue Container -->
                <div id="cluesListContainer" class="space-y-2.5 min-h-[100px]">
                    <!-- Injected via JS -->
                </div>

                <!-- Interactive Reaction Commentary Banner -->
                <div id="commentaryBanner" class="hidden p-3 rounded-2xl bg-slate-900 border text-center font-bold text-xs animate-pop">
                    <!-- Dynamic funny reaction string -->
                </div>

                <!-- Grid Opsi Jawaban -->
                <div id="optionsGrid" class="grid grid-cols-1 sm:grid-cols-2 gap-3 pt-1">
                    <!-- Injected via JS -->
                </div>

                <!-- Action Bar: Pass Question -->
                <div class="pt-3 border-t border-slate-800/80 flex justify-between items-center gap-3">
                    <div class="text-[11px] text-slate-400">
                        <span>Gak tau jawabannya?</span>
                    </div>

                    <button onclick="passQuestion()" id="passBtn" class="btn-bounce px-4 py-2.5 rounded-xl bg-slate-800 hover:bg-slate-700 text-orange-400 font-bold text-xs border border-orange-500/50 flex items-center gap-2 transition shadow-lg shadow-orange-950/30">
                        <i class="fa-solid fa-hand-holding-hand text-sm"></i> 
                        <span id="passBtnText">✋ Lempar ke Pemain 2</span>
                    </button>
                </div>

            </div>
        </section>

        <!-- SCREEN 3: RESULT SCREEN -->
        <section id="resultScreen" class="hidden w-full max-w-xl glass-card rounded-3xl p-6 sm:p-8 flex flex-col items-center gap-6 shadow-2xl border border-slate-800 text-center">
            
            <div id="winnerIcon" class="w-20 h-20 rounded-full bg-amber-500/20 border border-amber-500/50 flex items-center justify-center text-4xl text-amber-400 animate-bounce shadow-xl">
                ☕
            </div>

            <div class="space-y-1">
                <span class="text-xs uppercase tracking-widest font-bold text-slate-400">HASIL PERTANDINGAN JOKES</span>
                <h2 id="winnerText" class="font-game text-3xl sm:text-5xl font-bold text-amber-400">
                    PEMAIN 1 MENANG!
                </h2>
                <p id="winnerSubtitle" class="text-xs sm:text-sm text-slate-300">Raja Jokes Bapak-Bapak Paling Receh Se-Kecamatan!</p>
            </div>

            <!-- Skor Akhir -->
            <div class="w-full bg-slate-900/90 p-5 rounded-2xl border border-slate-800 grid grid-cols-2 gap-4">
                <div class="space-y-1">
                    <span id="resP1Name" class="text-xs font-bold text-blue-400 block uppercase tracking-wider">PEMAIN 1</span>
                    <span id="resP1Score" class="font-game text-4xl font-bold text-slate-100">0</span>
                    <span class="text-[10px] text-slate-400 block">Poin Receh</span>
                </div>
                <div class="space-y-1 border-l border-slate-800">
                    <span id="resP2Name" class="text-xs font-bold text-orange-400 block uppercase tracking-wider">PEMAIN 2</span>
                    <span id="resP2Score" class="font-game text-4xl font-bold text-slate-100">0</span>
                    <span class="text-[10px] text-slate-400 block">Poin Receh</span>
                </div>
            </div>

            <div class="flex flex-col sm:flex-row gap-3 w-full">
                <button onclick="startGame()" class="btn-bounce flex-1 py-3.5 rounded-xl bg-gradient-to-r from-amber-500 to-orange-500 hover:opacity-95 text-slate-950 font-game text-xl font-bold shadow-lg transition">
                    🔄 Main Lagi
                </button>
                <button onclick="resetToMenu()" class="btn-bounce flex-1 py-3.5 rounded-xl bg-slate-800 hover:bg-slate-700 text-slate-200 font-semibold text-sm border border-slate-700 transition">
                    ⚙️ Menu Utama
                </button>
            </div>

        </section>

    </main>

    <footer class="mt-4 text-center text-xs text-slate-500">
        Tebak Jokes Bapak-Bapak Duo • Pass & Play Local 2 Player
    </footer>

    <script>
        let audioCtx = null;
        let isSoundMuted = false;

        function initAudio() {
            if (!audioCtx) {
                audioCtx = new (window.AudioContext || window.webkitAudioContext)();
            }
            if (audioCtx && audioCtx.state === 'suspended') {
                audioCtx.resume();
            }
        }

        function toggleSound() {
            isSoundMuted = !isSoundMuted;
            const soundBtn = document.getElementById('soundBtn');
            if (soundBtn) {
                soundBtn.innerHTML = isSoundMuted 
                    ? '<i class="fa-solid fa-volume-xmark text-sm text-rose-400"></i>'
                    : '<i class="fa-solid fa-volume-high text-sm"></i>';
            }
        }

        function playSound(type) {
            if (isSoundMuted) return;
            initAudio();
            if (!audioCtx) return;

            const now = audioCtx.currentTime;

            if (type === 'clue') {
                const osc = audioCtx.createOscillator();
                const gain = audioCtx.createGain();
                osc.type = 'sine';
                osc.frequency.setValueAtTime(440, now);
                osc.frequency.exponentialRampToValueAtTime(880, now + 0.12);
                gain.gain.setValueAtTime(0.15, now);
                gain.gain.exponentialRampToValueAtTime(0.01, now + 0.12);
                osc.connect(gain);
                gain.connect(audioCtx.destination);
                osc.start(now);
                osc.stop(now + 0.12);
            } else if (type === 'correct') {
                // High-pitched funny victory chime
                [523.25, 659.25, 783.99, 1046.50, 1318.51].forEach((freq, idx) => {
                    const osc = audioCtx.createOscillator();
                    const gain = audioCtx.createGain();
                    osc.type = 'triangle';
                    osc.frequency.setValueAtTime(freq, now + idx * 0.06);
                    gain.gain.setValueAtTime(0.18, now + idx * 0.06);
                    gain.gain.exponentialRampToValueAtTime(0.001, now + idx * 0.06 + 0.2);
                    osc.connect(gain);
                    gain.connect(audioCtx.destination);
                    osc.start(now + idx * 0.06);
                    osc.stop(now + idx * 0.06 + 0.2);
                });
            } else if (type === 'wrong') {
                // Funny comedy fail pitch bend
                const osc = audioCtx.createOscillator();
                const gain = audioCtx.createGain();
                osc.type = 'sawtooth';
                osc.frequency.setValueAtTime(300, now);
                osc.frequency.exponentialRampToValueAtTime(80, now + 0.35);
                gain.gain.setValueAtTime(0.2, now);
                gain.gain.exponentialRampToValueAtTime(0.01, now + 0.35);
                osc.connect(gain);
                gain.connect(audioCtx.destination);
                osc.start(now);
                osc.stop(now + 0.35);
            } else if (type === 'pass') {
                const osc = audioCtx.createOscillator();
                const gain = audioCtx.createGain();
                osc.type = 'sine';
                osc.frequency.setValueAtTime(350, now);
                osc.frequency.linearRampToValueAtTime(220, now + 0.15);
                gain.gain.setValueAtTime(0.15, now);
                gain.gain.exponentialRampToValueAtTime(0.01, now + 0.15);
                osc.connect(gain);
                gain.connect(audioCtx.destination);
                osc.start(now);
                osc.stop(now + 0.15);
            } else if (type === 'drum') {
                // Drumroll synth
                for(let i = 0; i < 8; i++) {
                    const osc = audioCtx.createOscillator();
                    const gain = audioCtx.createGain();
                    osc.type = 'square';
                    osc.frequency.setValueAtTime(120 - i*5, now + i*0.05);
                    gain.gain.setValueAtTime(0.1, now + i*0.05);
                    gain.gain.exponentialRampToValueAtTime(0.01, now + i*0.05 + 0.04);
                    osc.connect(gain);
                    gain.connect(audioCtx.destination);
                    osc.start(now + i*0.05);
                    osc.stop(now + i*0.05 + 0.04);
                }
            } else if (type === 'laugh') {
                // Laughing synth pitches
                [300, 380, 320, 400, 350, 420].forEach((freq, idx) => {
                    const osc = audioCtx.createOscillator();
                    const gain = audioCtx.createGain();
                    osc.type = 'sine';
                    osc.frequency.setValueAtTime(freq, now + idx * 0.08);
                    gain.gain.setValueAtTime(0.12, now + idx * 0.08);
                    gain.gain.exponentialRampToValueAtTime(0.01, now + idx * 0.08 + 0.07);
                    osc.connect(gain);
                    gain.connect(audioCtx.destination);
                    osc.start(now + idx * 0.08);
                    osc.stop(now + idx * 0.08 + 0.07);
                });
            } else if (type === 'facepalm') {
                // Slide whistle down
                const osc = audioCtx.createOscillator();
                const gain = audioCtx.createGain();
                osc.type = 'sine';
                osc.frequency.setValueAtTime(600, now);
                osc.frequency.exponentialRampToValueAtTime(150, now + 0.3);
                gain.gain.setValueAtTime(0.15, now);
                gain.gain.exponentialRampToValueAtTime(0.01, now + 0.3);
                osc.connect(gain);
                gain.connect(audioCtx.destination);
                osc.start(now);
                osc.stop(now + 0.3);
            } else if (type === 'win') {
                // Victory Fanfare
                [523.25, 659.25, 783.99, 1046.50, 1318.51, 1567.98].forEach((freq, idx) => {
                    const osc = audioCtx.createOscillator();
                    const gain = audioCtx.createGain();
                    osc.type = 'triangle';
                    osc.frequency.setValueAtTime(freq, now + idx * 0.1);
                    gain.gain.setValueAtTime(0.2, now + idx * 0.1);
                    gain.gain.exponentialRampToValueAtTime(0.001, now + idx * 0.1 + 0.3);
                    osc.connect(gain);
                    gain.connect(audioCtx.destination);
                    osc.start(now + idx * 0.1);
                    osc.stop(now + idx * 0.1 + 0.3);
                });
            }
        }

        function triggerTaunt(type) {
            playSound(type);
            const box = document.getElementById('floatingReactionBox');
            const el = document.createElement('div');
            el.className = 'text-3xl sm:text-5xl font-black font-game text-amber-400 drop-shadow-lg animate-float';
            
            if (type === 'drum') el.innerText = '🥁 Ba-Dum-Tss!';
            else if (type === 'laugh') el.innerText = '😂 WKWKWK RECEH!';
            else if (type === 'facepalm') el.innerText = '🤦 ADUH SAKIT KEPALA!';

            box.appendChild(el);
            setTimeout(() => el.remove(), 800);
        }

        const mysteryDatabase = [
            // Kategori Plesetan Kata
            {
                cat: 'plesetan',
                catLabel: '☕ PLESETAN KATA',
                clues: [
                    'Kipas apa yang paling sering ditunggu-tunggu sama orang yang lagi PDKT?',
                    'Bukan kipas angin Dosen, bukan kipas bambu pasar malam.',
                    'Pasti yang kamu harapkan dari gebetan yang tidak peka-peka!'
                ],
                options: ['Kipas-tian (Kepastian)', 'Kipas Angin Portable', 'Kipas Sate', 'Kipas Maspion'],
                ans: 0,
                commentary: '☕ BAPAK-BAPAK APPROVED! Kipas-tian itu emang paling nyesek kalau gak ada!'
            },
            {
                cat: 'plesetan',
                catLabel: '☕ PLESETAN KATA',
                clues: [
                    'Lemari apa yang ukurannya sangat kecil sampai bisa kamu masukin ke kantong celana?',
                    'Bukan lemari pakaian anak kos, bukan juga lemari plastik.',
                    'Sering ditarik sama tukang parkir minimarket.'
                ],
                options: ['Lemaribu (Lima Ribu)', 'Lemari Es', 'Lemari Kayu', 'Lemari Plastik'],
                ans: 0,
                commentary: '💸 Lemaribu lembar merah ditarik tukang parkir dalam sekejap!'
            },
            {
                cat: 'plesetan',
                catLabel: '☕ PLESETAN KATA',
                clues: [
                    'Tahu apa yang ukurannya paling besar di seluruh muka bumi ini?',
                    'Bukan tahu isi pedas, bukan tahu sumedang hangat.',
                    'Setiap orang harus punya ini biar tidak kebangetan.'
                ],
                options: ['Tahu Diri', 'Tahu Sumedang', 'Tahu Crispy', 'Tahu Kedelai'],
                ans: 0,
                commentary: '🧠 Yang penting itu TAHU DIRI ya kawan-kawan!'
            },
            {
                cat: 'plesetan',
                catLabel: '☕ PLESETAN KATA',
                clues: [
                    'Kopi apa yang kalau diminum rasanya paling bikin dada nyesek dan sedih?',
                    'Bukan kopi hitam tanpa gula, bukan espresso pahit.',
                    'Hubungan kalian yang tidak direstui ortu.'
                ],
                options: ['Kopi-lih dia daripada aku', 'Kopi Tubruk', 'Kopi Luwak', 'Kopi Capucino'],
                ans: 0,
                commentary: '💔 Kopi-lih dia... aduh pedih banget rasanya!'
            },
            {
                cat: 'plesetan',
                catLabel: '☕ PLESETAN KATA',
                clues: [
                    'Awan apa yang bikin orang sedih banget dan langsung galau?',
                    'Bukan awan mendung mau hujan deres.',
                    'Rasanya pengen nangis di pojokan kamar.'
                ],
                options: ['Awan-na cry (I wanna cry)', 'Awan Cumulonimbus', 'Awan Kinton', 'Awan Putih'],
                ans: 0,
                commentary: '😭 Awan-na cry watching my e-wallet balance!'
            },

            // Kategori Hewan Receh
            {
                cat: 'hewan',
                catLabel: '🦎 HEWAN RECEH',
                clues: [
                    'Ikan apa yang matanya ada banyak banget, bisa sampai ratusan pasang mata?',
                    'Bukan ikan hiu raksasa, bukan juga ikan paus beluga.',
                    'Sering dijual asin dan dihitungnya per kilogram.'
                ],
                options: ['Ikan Teri 1 Kilogram', 'Ikan Gurame', 'Ikan Cupang', 'Ikan Hias'],
                ans: 0,
                commentary: '🐟 Mau berapa ribu mata teri tuh kalau sekilo?'
            },
            {
                cat: 'hewan',
                catLabel: '🦎 HEWAN RECEH',
                clues: [
                    'Kenapa nyamuk kalau terbang bunyinya selalu nging... nging... di dekat telinga?',
                    'Bukan karena mau bisik-bisik rahasia.',
                    'Coba pikirkan kalau dia minum air es batu...'
                ],
                options: ['Karna minumnya sirup (kalo es batu ngilu)', 'Karna mau bernyanyi', 'Karna kehabisan bensin', 'Karna suaranya merdu'],
                ans: 0,
                commentary: '🦟 Ngilu gigi nyamuknya kalau minum es batu!'
            },
            {
                cat: 'hewan',
                catLabel: '🦎 HEWAN RECEH',
                clues: [
                    'Ayam apa yang ukurannya paling besar di seluruh jagat raya ini?',
                    'Bukan ayam bangkok perkasa, bukan ayam jago tetangga.',
                    'Ada bintang, planet, dan galaksi di dalamnya.'
                ],
                options: ['Ayam Semesta (Alam Semesta)', 'Ayam Kampung', 'Ayam Geprek', 'Ayam Fillet'],
                ans: 0,
                commentary: '🌌 Ayam semesta beserta isinya!'
            },
            {
                cat: 'hewan',
                catLabel: '🦎 HEWAN RECEH',
                clues: [
                    'Kera apa yang kalau lagi naik sepeda motor bikin orang di jalanan deg-degan?',
                    'Bukan kera sakti Sun Wukong.',
                    'Namanya mirip banget sama kejadian kriminal.'
                ],
                options: ['Ke-Rampok!', 'Kera-jinan PR', 'Kera-sukan', 'Kera-jaan Mogok'],
                ans: 0,
                commentary: '🚨 Ke-Rampok di jalan raya bikin kaget!'
            },
            {
                cat: 'hewan',
                catLabel: '🦎 HEWAN RECEH',
                clues: [
                    'Gajah apa yang belalainya pendek banget tak sampai 5 centimeter?',
                    'Bukan gajah yang kena potong.',
                    'Sering kamu pakai pas sholat atau santai di rumah.'
                ],
                options: ['Gajah Duduk (Sarung)', 'Gajah Pesulap', 'Gajah Kedinginan', 'Gajah Miniatur'],
                ans: 0,
                commentary: '🕌 Sarung Gajah Duduk belalainya gak ada sama sekali malah!'
            },

            // Kategori Makanan & Sayur
            {
                cat: 'makanan',
                catLabel: '🥕 MAKANAN & SAYUR',
                clues: [
                    'Sayur apa yang memiliki pangkat dan jabatan sangat tinggi di angkatan militer?',
                    'Bukan kangkung tumis, bukan wortel rebus.',
                    'Pangkat di atas kapten dan di bawah letnan kolonel.'
                ],
                options: ['Sayur Mayor (Major)', 'Sayur Bayam', 'Sayur Lodeh', 'Sayur Asem'],
                ans: 0,
                commentary: '🎖️ Siap Komandan Sayur Mayor!'
            },
            {
                cat: 'makanan',
                catLabel: '🥕 MAKANAN & SAYUR',
                clues: [
                    'Roti apa yang tidak pernah merasa lapar sama sekali walaupun didiamkan seharian?',
                    'Bukan roti bakar cokelat, bukan roti tawar gandum.',
                    'Jawaban ini sangat logis dan tidak bisa dibantah!'
                ],
                options: ['Roti-dak pernah lapar (Roti-dak)', 'Roti Sobek', 'Roti Keju', 'Roti Cane'],
                ans: 0,
                commentary: '🍞 Roti-dak pernah lapar ya jelas dong!'
            },
            {
                cat: 'makanan',
                catLabel: '🥕 MAKANAN & SAYUR',
                clues: [
                    'Sayur apa yang kalau dinyanyikan suaranya merdu banget kayak band papan atas dunia?',
                    'Bukan sawi hijau, bukan juga terong ungu.',
                    'Pelantun lagu hits "Yellow" & "Fix You".'
                ],
                options: ['Kembang Kol (Coldplay)', 'Bayam Rock', 'Kangkung Pop', 'Sawi Jazz'],
                ans: 0,
                commentary: '🎤 Look at the stars, look how they shine for Kembang Kol!'
            },
            {
                cat: 'makanan',
                catLabel: '🥕 MAKANAN & SAYUR',
                clues: [
                    'Nasi apa yang tidak pernah bisa kamu makan sama sekali seumur hidupmu?',
                    'Bukan nasi goreng pedas, bukan nasi uduk hangat.',
                    'Sering disampaikan sama bapak dan ibu guru.'
                ],
                options: ['Nasi-hat Orang Tua', 'Nasi Padang', 'Nasi Kuning', 'Nasi Kebuli'],
                ans: 0,
                commentary: '👴 Nasi-hat ortu tuh didengarkan, jangan dimakan!'
            },

            // Kategori Kehidupan Bapak
            {
                cat: 'sehari',
                catLabel: '🚗 KEHIDUPAN BAPAK',
                clues: [
                    'Sepatu apa yang paling tidak bisa dipakai berjalan sama sekali?',
                    'Bukan sepatu kekecilan, bukan sepatu rusak.',
                    'Paling sering diucapkan bapak-bapak saat musyawarah RT.'
                ],
                options: ['Sepatu-ju (Setuju)', 'Sepatu Lari', 'Sepatu Boot', 'Sepatu Futsal'],
                ans: 0,
                commentary: '🤝 "Saya Sepatu-ju sama Pak RT!"'
            },
            {
                cat: 'sehari',
                catLabel: '🚗 KEHIDUPAN BAPAK',
                clues: [
                    'Mobil apa yang paling bikin kaget dan jantungan saat mendengarnya?',
                    'Bukan mobil balap F1, bukan mobil pemadam kebakaran.',
                    'Kata-kata dari pacar saat mau putus.'
                ],
                options: ['Mobil-ang "Kita Putus Ya"', 'Mobil Lamborghini', 'Mobil Truk Oleng', 'Mobil Ambulans'],
                ans: 0,
                commentary: '💔 Mobil-ang putus langsung jantungan parah!'
            },
            {
                cat: 'sehari',
                catLabel: '🚗 KEHIDUPAN BAPAK',
                clues: [
                    'Jam apa yang paling bikin cemas dan bikin stres anak muda zaman sekarang?',
                    'Bukan jam dinding mati, bukan jam tangan mahal.',
                    'Kondisi kehidupan saat cari kerja susah.'
                ],
                options: ['Jam-an Sekarang Cari Kerja Susah', 'Jam Beker', 'Jam Pasang', 'Jam Dinding'],
                ans: 0,
                commentary: '⏰ Realistis banget ya jokes bapak yang ini!'
            },

            // Kategori Pop & Musik
            {
                cat: 'pop',
                catLabel: '🎬 POP & MUSIK RECEH',
                clues: [
                    'Penyanyi internasional yang hobi banget jualan Bumbu Nasi Goreng keliling?',
                    'Bukan Ariana Grande, bukan Taylor Swift.',
                    'Pelantun lagu "Baby" waktu masih remaja.'
                ],
                options: ['Justin Bumbu (Justin Bieber)', 'Ed Sheerun', 'Bruno Mars', 'Drake'],
                ans: 0,
                commentary: '🍳 Justin Bumbu spesial pakai telur dua!'
            },
            {
                cat: 'pop',
                catLabel: '🎬 POP & MUSIK RECEH',
                clues: [
                    'Penyanyi dangdut Indonesia yang paling sering kena flu dan masuk angin?',
                    'Bukan Inul Daratista, bukan Rhoma Irama.',
                    'Tiap nyanyi batu-batuk terus.'
                ],
                options: ['Ari Lasso (Ari Flu / Batuk)', 'Siti Badriah', 'Ayu Ting Ting', 'Via Vallen'],
                ans: 0,
                commentary: '🤧 Batuk-batuk melulu pas manggung!'
            }
        ];

        let p1Name = "Bapak Agus";
        let p2Name = "Bapak Bambang";
        let p1Score = 0;
        let p2Score = 0;

        let selectedCat = 'all';
        let totalRounds = 10;

        let activeMysteries = [];
        let currentRound = 0;
        let currentPlayer = 1; 
        let currentClueLevel = 0; 
        let currentPointsValue = 30; 
        let isPassed = false;

        function selectCategory(cat) {
            selectedCat = cat;
            document.querySelectorAll('.cat-btn').forEach(btn => {
                btn.className = 'cat-btn bg-slate-800/80 border border-slate-700 hover:border-slate-500 text-slate-300 p-3 rounded-2xl text-xs font-bold transition flex flex-col items-center gap-1.5';
            });

            const activeBtn = document.getElementById(`cat-${cat}`);
            if (activeBtn) {
                activeBtn.className = 'cat-btn bg-amber-600 border-2 border-amber-400 text-white p-3 rounded-2xl text-xs font-bold transition flex flex-col items-center gap-1.5 shadow-lg shadow-amber-950/50';
            }
        }

        function startGame() {
            initAudio();

            p1Name = document.getElementById('p1NameInput').value.trim() || "Pemain 1";
            p2Name = document.getElementById('p2NameInput').value.trim() || "Pemain 2";
            totalRounds = parseInt(document.getElementById('questionCountSelect').value);

            let pool = selectedCat === 'all' 
                ? [...mysteryDatabase] 
                : mysteryDatabase.filter(m => m.cat === selectedCat);

            // Shuffle pool
            pool.sort(() => Math.random() - 0.5);
            activeMysteries = pool.slice(0, Math.min(totalRounds, pool.length));

            p1Score = 0;
            p2Score = 0;
            currentRound = 0;
            currentPlayer = 1;
            isPassed = false;

            document.getElementById('p1NameLabel').innerText = p1Name;
            document.getElementById('p2NameLabel').innerText = p2Name;
            document.getElementById('p1Score').innerText = '0';
            document.getElementById('p2Score').innerText = '0';

            document.getElementById('menuScreen').classList.add('hidden');
            document.getElementById('resultScreen').classList.add('hidden');
            document.getElementById('gameScreen').classList.remove('hidden');

            loadRound();
        }

        function loadRound() {
            if (currentRound >= activeMysteries.length) {
                finishGame();
                return;
            }

            const mData = activeMysteries[currentRound];
            currentClueLevel = 0;
            currentPointsValue = 30;
            isPassed = false;

            document.getElementById('categoryBadge').innerText = mData.catLabel;
            document.getElementById('questionTracker').innerText = `Ronde ${currentRound + 1} / ${activeMysteries.length}`;
            document.getElementById('rewardPointsBadge').innerText = `💎 Nilai: ${currentPointsValue} Poin`;

            document.getElementById('commentaryBanner').classList.add('hidden');

            renderClues();
            renderOptions();
            updateTurnUI();
        }

        function renderClues() {
            const mData = activeMysteries[currentRound];
            const container = document.getElementById('cluesListContainer');
            container.innerHTML = '';

            for (let i = 0; i <= currentClueLevel; i++) {
                const div = document.createElement('div');
                div.className = `p-3.5 rounded-2xl border text-xs sm:text-sm font-medium flex items-start gap-3 animate-pop ${
                    i === 0 ? 'bg-amber-950/40 border-amber-800/60 text-amber-200' :
                    i === 1 ? 'bg-orange-950/40 border-orange-800/60 text-orange-200' :
                    'bg-yellow-950/40 border-yellow-800/60 text-yellow-200'
                }`;
                div.innerHTML = `
                    <span class="w-6 h-6 rounded-lg bg-slate-900 border border-slate-700 flex items-center justify-center font-bold text-xs shrink-0 font-mono text-amber-400">
                        #${i + 1}
                    </span>
                    <span class="leading-relaxed">${mData.clues[i]}</span>
                `;
                container.appendChild(div);
            }

            const revealBtn = document.getElementById('revealClueBtn');
            const nextNum = document.getElementById('nextClueNum');
            if (currentClueLevel >= 2) {
                revealBtn.classList.add('hidden');
            } else {
                revealBtn.classList.remove('hidden');
                nextNum.innerText = currentClueLevel + 2;
            }
        }

        function revealNextClue() {
            if (currentClueLevel < 2) {
                playSound('clue');
                currentClueLevel++;
                currentPointsValue = currentClueLevel === 1 ? 20 : 10;
                document.getElementById('rewardPointsBadge').innerText = `💎 Nilai: ${currentPointsValue} Poin`;
                renderClues();
            }
        }

        function renderOptions() {
            const mData = activeMysteries[currentRound];
            const optionsGrid = document.getElementById('optionsGrid');
            optionsGrid.innerHTML = '';

            let optsWithIndex = mData.options.map((opt, idx) => ({ text: opt, isCorrect: idx === mData.ans }));
            optsWithIndex.sort(() => Math.random() - 0.5);

            optsWithIndex.forEach((item, idx) => {
                const btn = document.createElement('button');
                btn.className = 'btn-bounce bg-slate-800/90 hover:bg-slate-700/80 border border-slate-700 text-slate-100 p-3.5 sm:p-4 rounded-2xl text-left text-xs sm:text-sm font-semibold transition flex items-center justify-between group shadow-md';
                btn.innerHTML = `
                    <span>${item.text}</span>
                    <span class="w-6 h-6 rounded-full bg-slate-900 text-xs text-slate-400 group-hover:text-amber-400 flex items-center justify-center border border-slate-700 font-mono">
                        ${String.fromCharCode(65 + idx)}
                    </span>
                `;
                btn.onclick = () => handleAnswer(item.isCorrect, btn, optsWithIndex);
                optionsGrid.appendChild(btn);
            });
        }

        function updateTurnUI() {
            const p1Card = document.getElementById('p1Card');
            const p2Card = document.getElementById('p2Card');
            const p1Badge = document.getElementById('p1Badge');
            const p2Badge = document.getElementById('p2Badge');
            const turnIndicator = document.getElementById('turnIndicator');
            const passBtnText = document.getElementById('passBtnText');
            const stealBadge = document.getElementById('stealBadge');

            if (currentPlayer === 1) {
                p1Card.className = 'glass-card p-3.5 sm:p-4 rounded-2xl border-2 p1-border flex items-center justify-between transition-all scale-105 shadow-xl shadow-blue-950/40';
                p2Card.className = 'glass-card p-3.5 sm:p-4 rounded-2xl border-2 border-transparent flex items-center justify-between transition-all opacity-60';
                
                p1Badge.className = 'w-10 h-10 rounded-xl p1-gradient flex items-center justify-center font-bold text-white shadow-md text-sm';
                p2Badge.className = 'w-10 h-10 rounded-xl bg-slate-800 flex items-center justify-center font-bold text-slate-400 shadow-md text-sm';

                turnIndicator.className = 'px-3 py-1.5 rounded-full font-bold p1-gradient text-white shadow-md text-xs';
                turnIndicator.innerText = `🎯 GILIRAN: ${p1Name.toUpperCase()}`;
                passBtnText.innerText = `✋ Lempar ke ${p2Name}`;
            } else {
                p2Card.className = 'glass-card p-3.5 sm:p-4 rounded-2xl border-2 p2-border flex items-center justify-between transition-all scale-105 shadow-xl shadow-orange-950/40';
                p1Card.className = 'glass-card p-3.5 sm:p-4 rounded-2xl border-2 border-transparent flex items-center justify-between transition-all opacity-60';

                p2Badge.className = 'w-10 h-10 rounded-xl p2-gradient flex items-center justify-center font-bold text-white shadow-md text-sm';
                p1Badge.className = 'w-10 h-10 rounded-xl bg-slate-800 flex items-center justify-center font-bold text-slate-400 shadow-md text-sm';

                turnIndicator.className = 'px-3 py-1.5 rounded-full font-bold p2-gradient text-white shadow-md text-xs';
                turnIndicator.innerText = `🎯 GILIRAN: ${p2Name.toUpperCase()}`;
                passBtnText.innerText = `✋ Lempar ke ${p1Name}`;
            }

            if (isPassed) {
                stealBadge.classList.remove('hidden');
                document.getElementById('passBtn').disabled = true;
                document.getElementById('passBtn').classList.add('opacity-40', 'cursor-not-allowed');
            } else {
                stealBadge.classList.add('hidden');
                document.getElementById('passBtn').disabled = false;
                document.getElementById('passBtn').classList.remove('opacity-40', 'cursor-not-allowed');
            }
        }

        function handleAnswer(isCorrect, clickedBtn, allOpts) {
            const optionsGrid = document.getElementById('optionsGrid');
            const buttons = optionsGrid.children;

            for (let btn of buttons) {
                btn.disabled = true;
            }

            const mData = activeMysteries[currentRound];
            const commBanner = document.getElementById('commentaryBanner');

            if (isCorrect) {
                playSound('correct');
                clickedBtn.classList.remove('bg-slate-800/90');
                clickedBtn.classList.add('bg-emerald-600', 'border-emerald-400', 'text-white', 'scale-105');

                const finalAdd = isPassed ? currentPointsValue + 5 : currentPointsValue;

                if (currentPlayer === 1) {
                    p1Score += finalAdd;
                    document.getElementById('p1Score').innerText = p1Score;
                } else {
                    p2Score += finalAdd;
                    document.getElementById('p2Score').innerText = p2Score;
                }

                commBanner.innerText = mData.commentary || '☕ BAPAK-BAPAK APPROVED! Garingnya dapet!';
                commBanner.className = 'p-3 rounded-2xl bg-emerald-950/80 border border-emerald-700 text-emerald-300 font-bold text-xs sm:text-sm animate-pop';
                commBanner.classList.remove('hidden');

            } else {
                playSound('wrong');
                clickedBtn.classList.remove('bg-slate-800/90');
                clickedBtn.classList.add('bg-rose-600', 'border-rose-400', 'text-white', 'animate-shake');

                for (let i = 0; i < buttons.length; i++) {
                    if (allOpts[i].isCorrect) {
                        buttons[i].classList.remove('bg-slate-800/90');
                        buttons[i].classList.add('bg-emerald-700/80', 'border-emerald-400', 'text-white');
                    }
                }

                commBanner.innerText = '🤦 ADUH SALAH TEBAK! Bikin pusing bapak-bapak aja!';
                commBanner.className = 'p-3 rounded-2xl bg-rose-950/80 border border-rose-700 text-rose-300 font-bold text-xs sm:text-sm animate-pop';
                commBanner.classList.remove('hidden');
            }

            setTimeout(() => {
                nextRound();
            }, 2200);
        }

        function passQuestion() {
            if (isPassed) return;
            playSound('pass');
            isPassed = true;
            currentPlayer = currentPlayer === 1 ? 2 : 1;
            updateTurnUI();
        }

        function nextRound() {
            currentRound++;
            isPassed = false;
            currentPlayer = (currentRound % 2 === 0) ? 1 : 2;
            loadRound();
        }

        function finishGame() {
            playSound('win');

            document.getElementById('gameScreen').classList.add('hidden');
            document.getElementById('resultScreen').classList.remove('hidden');

            document.getElementById('resP1Name').innerText = p1Name;
            document.getElementById('resP2Name').innerText = p2Name;
            document.getElementById('resP1Score').innerText = p1Score;
            document.getElementById('resP2Score').innerText = p2Score;

            const winnerText = document.getElementById('winnerText');
            const winnerIcon = document.getElementById('winnerIcon');
            const winnerSubtitle = document.getElementById('winnerSubtitle');

            if (p1Score > p2Score) {
                winnerText.innerText = `${p1Name.toUpperCase()} MENANG! 🎉`;
                winnerText.className = "font-game text-3xl sm:text-5xl font-bold text-blue-400";
                winnerIcon.innerText = "👑";
                winnerSubtitle.innerText = `${p1Name} resmi menyandang gelar Raja Jokes Bapak-Bapak Receh!`;
            } else if (p2Score > p1Score) {
                winnerText.innerText = `${p2Name.toUpperCase()} MENANG! 🎉`;
                winnerText.className = "font-game text-3xl sm:text-5xl font-bold text-orange-400";
                winnerIcon.innerText = "👑";
                winnerSubtitle.innerText = `${p2Name} paling menguasai ilmu garing bapak-bapak!`;
            } else {
                winnerText.innerText = "HASIL SERI! ☕";
                winnerText.className = "font-game text-3xl sm:text-5xl font-bold text-amber-400";
                winnerIcon.innerText = "🤝";
                winnerSubtitle.innerText = "Dua-duanya sama-sama receh dan bikin pusing!";
            }
        }

        function resetToMenu() {
            document.getElementById('gameScreen').classList.add('hidden');
            document.getElementById('resultScreen').classList.add('hidden');
            document.getElementById('menuScreen').classList.remove('hidden');
        }
    </script>
</body>
</html>
