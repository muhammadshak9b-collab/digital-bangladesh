<!DOCTYPE html>  <html lang="bn">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <title>আমার ডিজিটাল বাংলাদেশ | Digital Bangladesh</title>  <!-- Tailwind CSS -->  
<script src="https://cdn.tailwindcss.com"></script>  
  
<!-- Font Awesome Icons -->  
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">  
  
<!-- Google Fonts -->  
<link href="https://fonts.googleapis.com/css2?family=Hind+Siliguri:wght@500;600;700;800&family=Plus+Jakarta+Sans:wght@600;700;800;900&display=swap" rel="stylesheet">  
  
<!-- html2canvas -->  
<script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>  

<style>  
    body {  
        font-family: 'Hind Siliguri', 'Plus Jakarta Sans', sans-serif;  
        background-color: #f8fafc;  
        color: #000000;  
    }  

    .glass-card {  
        background: rgba(255, 255, 255, 0.98);  
        backdrop-filter: blur(16px);  
        border: 1px solid rgba(16, 185, 129, 0.2);  
        box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.05);  
    }  

    /* Compact App Card Design */  
    .app-card {  
        transition: all 0.2s ease;  
        background-color: #ffffff;  
        border: 1.5px solid #cbd5e1;  
        padding: 0.5rem 0.65ln;  
    }  
    .app-card:hover {  
        transform: translateY(-2px);  
        border-color: #059669;  
        box-shadow: 0 4px 12px rgba(5, 150, 105, 0.15);  
    }  

    .app-checkbox:checked + .app-card {  
        border-color: #059669;  
        background-color: #ecfdf5;  
    }  

    .app-checkbox:checked + .app-card .check-badge {  
        display: flex;  
    }  

    /* Compact Facebook Poster Canvas (1000x520 px) */  
    #facebookCardCanvas {  
        width: 1000px;  
        height: 520px;  
        background: linear-gradient(135deg, #064e3b 0%, #047857 50%, #10b981 100%);  
        color: #ffffff !important;  
    }  
    #facebookCardCanvas * {  
        color: #ffffff !important;  
    }  
    #facebookCardCanvas .text-accent {  
        color: #facc15 !important;  
    }  
</style>

</head>  
<body class="min-h-screen flex flex-col justify-between">  <!-- Top Navigation Bar -->  
<header class="bg-white sticky top-0 z-50 border-b border-emerald-100 shadow-sm">  
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-3 flex items-center justify-between">  
        <div class="flex items-center space-x-3 space-x-reverse">  
            <div class="w-10 h-10 rounded-xl bg-emerald-600 text-white flex items-center justify-center text-xl shadow-md shadow-emerald-200">  
                <i class="fa-solid fa-mobile-screen-button"></i>  
            </div>  
            <div>  
                <h1 id="navTitle" class="text-lg font-black text-black leading-tight">  
                    আমার ডিজিটাল বাংলাদেশ  
                </h1>  
                <p id="navSubtitle" class="text-[10px] text-slate-800 font-bold uppercase tracking-wider">Digital Bangladesh</p>  
            </div>  
        </div>  

        <div class="flex items-center space-x-3">  
            <button id="langToggleBtn" onclick="toggleLanguage()" class="px-3.5 py-1.5 rounded-lg border border-emerald-300 bg-emerald-50 text-black text-xs font-bold hover:bg-emerald-100 transition shadow-sm">  
                <i class="fa-solid fa-language mr-1"></i> English  
            </button>  
        </div>  
    </div>  
</header>  

<!-- Main Content -->  
<main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-6 w-full space-y-6">  

    <!-- Hero Header -->  
    <section class="glass-card rounded-3xl p-5 sm:p-7 flex flex-col md:flex-row items-center justify-between gap-6 border-2 border-emerald-100">  
        <div class="space-y-2 text-center md:text-left">  
            <span id="heroBadge" class="inline-block px-3 py-1 rounded-full bg-emerald-100 text-emerald-900 text-[11px] font-black uppercase tracking-wider">  
                ⚡ ডিজিটাল বাংলাদেশ অ্যাপস ট্র্যাকার (১০০+ অ্যাপস)  
            </span>  
            <h2 id="heroTitle" class="text-2xl sm:text-3xl font-black text-black leading-tight">  
                আপনি ডিজিটাল দুনিয়ায় কত পার্সেন্ট আছেন?  
            </h2>  
            <p id="heroDesc" class="text-black text-xs sm:text-sm font-semibold max-w-2xl leading-relaxed">  
                নিচের প্রতিটি ক্যাটাগরি থেকে আপনার ব্যবহৃত অ্যাপসগুলোতে টিক দিন এবং নিচে আপনার নাম ও গোল সুন্দর ছবি আপলোড করে কাস্টম পোস্টার তৈরি করুন।  
            </p>  
        </div>  

        <!-- Live Adoption Progress Meter -->  
        <div class="bg-gradient-to-br from-emerald-600 to-teal-700 text-white p-5 rounded-2xl text-center shadow-lg w-full md:w-56 flex-shrink-0">  
            <span id="scoreLabel" class="text-[10px] font-bold uppercase tracking-wider opacity-90 block text-white">লাইভ এডাপশন স্কোর</span>  
            <div class="text-3xl font-black my-1 text-yellow-300" id="heroLiveScore">0%</div>  
            <div class="w-full bg-black/30 rounded-full h-2.5 overflow-hidden mt-1.5">  
                <div id="heroScoreBar" class="bg-yellow-400 h-2.5 rounded-full transition-all duration-500" style="width: 0%"></div>  
            </div>  
        </div>  
    </section>  

    <!-- App Search Bar -->  
    <section class="glass-card p-3.5 rounded-2xl flex flex-col sm:flex-row items-center justify-between gap-3">  
        <div class="relative w-full sm:w-80">  
            <i class="fa-solid fa-magnifying-glass absolute left-3 top-3 text-slate-500 text-xs"></i>  
            <input type="text" id="appSearchInput" onkeyup="filterApps()" placeholder="অ্যাপের নাম দিয়ে খুঁজুন..." class="w-full pl-9 pr-3 py-2 text-xs bg-white border-2 border-slate-300 rounded-xl focus:outline-none focus:ring-2 focus:ring-emerald-500 text-black font-bold">  
        </div>  

        <div class="flex items-center space-x-2 w-full sm:w-auto justify-end">  
            <button id="selectAllBtn" onclick="selectAllApps(true)" class="px-3.5 py-2 text-xs font-bold text-black bg-emerald-100 border border-emerald-300 rounded-xl hover:bg-emerald-200 transition">  
                সব সিলেক্ট করুন  
            </button>  
            <button id="resetBtn" onclick="selectAllApps(false)" class="px-3.5 py-2 text-xs font-bold text-black bg-rose-100 border border-rose-300 rounded-xl hover:bg-rose-200 transition">  
                রিসেট করুন  
            </button>  
        </div>  
    </section>  

    <!-- Apps Selection Grid Container -->  
    <section id="appsCategoriesContainer" class="space-y-6"></section>  

    <!-- Profile & Photo Card Controls -->  
    <section class="glass-card rounded-3xl p-5 sm:p-7 space-y-5 border-2 border-emerald-500/40">  
        <div class="border-b border-slate-200 pb-3 text-center md:text-left">  
            <h3 id="cardMakerTitle" class="text-lg font-black text-black flex items-center justify-center md:justify-start gap-2">  
                <i class="fa-solid fa-id-card text-emerald-600"></i>  
                কাস্টমাইজড প্রোফাইল ও গোল ফটো কার্ড মেকার  
            </h3>  
            <p id="cardMakerDesc" class="text-xs text-black font-bold mt-1">আপনার নাম লিখুন এবং ছবি আপলোড করুন (ছবিটি কার্ডে সুন্দর গোলাকার ফ্রেমের মধ্যে থাকবে)</p>  
        </div>  

        <div class="grid grid-cols-1 md:grid-cols-2 gap-5">  
            <div>  
                <label id="labelName" class="block text-xs font-black text-black mb-1.5">আপনার নাম (কার্ডে দেখাবে)</label>  
                <input type="text" id="inputUserName" oninput="saveUserData()" placeholder="যেমন: সাকিব হাসান" class="w-full px-3.5 py-2 rounded-xl border-2 border-slate-300 bg-white text-xs font-bold focus:outline-none focus:ring-2 focus:ring-emerald-500 text-black">  
            </div>  

            <div>  
                <label id="labelPhoto" class="block text-xs font-black text-black mb-1.5">আপনার সুন্দর ছবি আপলোড করুন</label>  
                <input type="file" id="inputUserPhoto" accept="image/*" class="w-full text-xs text-black font-bold file:mr-3 file:py-2 file:px-3 file:rounded-lg file:border-0 file:text-xs file:font-bold file:bg-emerald-100 file:text-black hover:file:bg-emerald-200 bg-white rounded-xl border-2 border-slate-300">  
            </div>  
        </div>  

        <div class="text-center pt-2">  
            <button id="generateBtn" onclick="generatePhotoCard()" class="px-8 py-3.5 bg-gradient-to-r from-emerald-600 via-teal-600 to-emerald-700 hover:from-emerald-700 hover:to-teal-800 text-white font-black rounded-2xl shadow-xl shadow-emerald-200 text-sm sm:text-base transition transform hover:-translate-y-1">  
                <i class="fa-solid fa-wand-magic-sparkles mr-2"></i> পোস্ট ফটো কার্ড তৈরি করুন  
            </button>  
        </div>  
    </section>  

    <!-- Compact Facebook Post Canvas Preview Modal -->  
    <section id="cardPreviewModal" class="hidden bg-slate-900/80 fixed inset-0 z-50 flex items-center justify-center p-4 overflow-y-auto backdrop-blur-sm">  
        <div class="glass-card rounded-3xl p-5 max-w-4xl w-full space-y-5 max-h-[90vh] overflow-y-auto">  
            <div class="flex items-center justify-between border-b border-slate-200 pb-2.5">  
                <h3 id="modalHeaderTitle" class="text-base font-black text-black">আপনার কাস্টম ডিজিটাল ফটো কার্ড</h3>  
                <button onclick="closeModal()" class="text-slate-500 hover:text-black text-lg font-bold px-2">✕</button>  
            </div>  

            <!-- Compact Perfect-Sized Canvas (1000x520) -->  
            <div class="overflow-x-auto flex justify-center py-2">  
                <div id="facebookCardCanvas" class="p-8 flex flex-col justify-between relative shadow-2xl rounded-3xl border-4 border-white/20">  
                      
                    <!-- Top Bar -->  
                    <div class="flex items-center justify-between border-b border-white/20 pb-4">  
                        <div class="flex items-center space-x-3">  
                            <div class="w-12 h-12 rounded-xl bg-white/10 backdrop-blur-md border border-white/20 flex items-center justify-center text-2xl">  
                                <i class="fa-solid fa-mobile-screen-button text-accent"></i>  
                            </div>  
                            <div>  
                                <h4 id="canvasTitle" class="text-2xl font-black">আমার ডিজিটাল বাংলাদেশ</h4>  
                                <p id="canvasSubtitle" class="text-xs font-semibold uppercase tracking-widest text-emerald-200">Digital Bangladesh</p>  
                            </div>  
                        </div>  
                        <div id="canvasBadgeText" class="px-4 py-2 rounded-full bg-white/10 backdrop-blur-md border border-white/20 text-xs font-bold text-accent uppercase tracking-wider">  
                            🇧🇩 ডিজিটাল নাগরিক  
                        </div>  
                    </div>  

                    <!-- Center Profile Section -->  
                    <div class="flex items-center justify-center gap-10 my-4">  
                        <div class="relative flex-shrink-0">  
                            <div class="w-32 h-32 rounded-full border-4 border-yellow-400 p-1 bg-white/10 shadow-2xl overflow-hidden">  
                                <img id="cardUserProfileImg" src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?w=200" class="w-full h-full rounded-full object-cover">  
                            </div>  
                            <div class="absolute bottom-0 right-0 bg-emerald-500 text-white w-9 h-9 rounded-full flex items-center justify-center text-sm border-2 border-white shadow">  
                                <i class="fa-solid fa-check"></i>  
                            </div>  
                        </div>  

                        <div class="space-y-3">  
                            <h5 id="cardUserNameText" class="text-3xl font-black">সাকিব হাসান</h5>  
                            <div class="inline-flex items-center space-x-3 px-5 py-2.5 bg-black/40 backdrop-blur-md rounded-2xl border border-white/20">  
                                <span id="canvasScoreLabel" class="text-sm font-semibold">ডিজিটাল এ্যাডাপশন স্কোর:</span>  
                                <span id="cardScorePercent" class="text-4xl font-black text-accent">0%</span>  
                            </div>  
                        </div>  
                    </div>  

                    <!-- Footer -->  
                    <div class="flex items-center justify-between border-t border-white/20 pt-4 text-xs text-emerald-100">  
                        <div><span class="font-bold">Website:</span> Digital Bangladesh</div>  
                        <div class="font-bold">Developed by <span class="text-accent">Mohammad Nazmus Shakib</span></div>  
                    </div>  
                </div>  
            </div>  

            <div class="flex flex-col sm:flex-row items-center justify-end gap-3 pt-2 border-t border-slate-200">  
                <button id="downloadBtn" onclick="downloadCardImage()" class="w-full sm:w-auto px-6 py-3 bg-emerald-600 hover:bg-emerald-700 text-white font-bold rounded-xl text-xs sm:text-sm transition shadow-lg">  
                    <i class="fa-solid fa-download mr-1.5"></i> এইচডি ফটো ডাউনলোড করুন (PNG)  
                </button>  
                <button id="closeModalBtn" onclick="closeModal()" class="w-full sm:w-auto px-5 py-3 bg-slate-200 text-black font-bold rounded-xl text-xs sm:text-sm transition">  
                    বন্ধ করুন  
                </button>  
            </div>  
        </div>  
    </section>  

    <!-- Formspree Contact Form -->  
    <section class="glass-card rounded-3xl p-5 sm:p-7 max-w-3xl mx-auto border-2 border-slate-200">  
        <div class="text-center space-y-1.5 mb-5">  
            <h3 id="contactHeading" class="text-xl font-black text-black">আমাদের সাথে যোগাযোগ করুন</h3>  
            <p id="contactSub" class="text-xs text-black font-semibold">নতুন অ্যাপ যুক্ত করা বা যেকোনো প্রশ্নের জন্য ইমেইল পাঠান।</p>  
        </div>  

        <form action="https://formspree.io/f/xjyvbbag" method="POST" class="space-y-3.5">  
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-3.5">  
                <div>  
                    <label id="formNameLabel" class="block text-xs font-black text-black mb-1">আপনার নাম</label>  
                    <input type="text" name="name" required placeholder="আপনার নাম লিখুন" class="w-full px-3.5 py-2 rounded-xl border-2 border-slate-300 text-xs font-bold focus:outline-none focus:ring-2 focus:ring-emerald-500 bg-white text-black">  
                </div>  
                <div>  
                    <label id="formEmailLabel" class="block text-xs font-black text-black mb-1">আপনার ইমেইল</label>  
                    <input type="email" name="email" required placeholder="example@gmail.com" class="w-full px-3.5 py-2 rounded-xl border-2 border-slate-300 text-xs font-bold focus:outline-none focus:ring-2 focus:ring-emerald-500 bg-white text-black">  
                </div>  
            </div>  
            <div>  
                <label id="formMsgLabel" class="block text-xs font-black text-black mb-1">বার্তা বা পরামর্শ</label>  
                <textarea name="message" rows="3" required placeholder="এখানে আপনার বার্তা লিখুন..." class="w-full px-3.5 py-2 rounded-xl border-2 border-slate-300 text-xs font-bold focus:outline-none focus:ring-2 focus:ring-emerald-500 bg-white text-black"></textarea>  
            </div>  
            <button type="submit" id="formSubmitBtn" class="w-full py-3 bg-emerald-600 hover:bg-emerald-700 text-white font-bold rounded-xl text-xs transition shadow-md shadow-emerald-200">  
                <i class="fa-solid fa-paper-plane mr-1.5"></i> বার্তা পাঠান (Formspree)  
            </button>  
        </form>  
    </section>  

</main>  

<!-- Footer -->  
<footer class="bg-white border-t border-slate-200 py-5 text-center text-xs text-black font-semibold mt-10">  
    <p id="footerCopy">© 2026 Digital Bangladesh. All Rights Reserved.</p>  
    <p class="mt-1 font-extrabold text-black">Developed with ❤️ by <span class="text-emerald-700 font-black">Mohammad Nazmus Shakib</span></p>  
</footer>  

<script>  
    // 🔹 Dual Language App Database (Bengali & English)  
    const appDatabase = [  
        // 1. FinTech & Banking  
        { id: "bkash", name: { bn: "বিকাশ", en: "bKash" }, category: "fintech", icon: "fa-solid fa-wallet", color: "text-pink-600 bg-pink-100" },  
        { id: "nagad", name: { bn: "নগদ", en: "Nagad" }, category: "fintech", icon: "fa-solid fa-money-bill-transfer", color: "text-orange-600 bg-orange-100" },  
        { id: "rocket", name: { bn: "রকেট", en: "Rocket" }, category: "fintech", icon: "fa-solid fa-building-columns", color: "text-purple-600 bg-purple-100" },  
        { id: "upay", name: { bn: "উপায়", en: "Upay" }, category: "fintech", icon: "fa-solid fa-mobile-screen", color: "text-blue-600 bg-blue-100" },  
        { id: "cellfin", name: { bn: "সেলফিন", en: "CellFin" }, category: "fintech", icon: "fa-solid fa-landmark", color: "text-emerald-600 bg-emerald-100" },  
        { id: "tap", name: { bn: "ট্যাপ", en: "Tap" }, category: "fintech", icon: "fa-solid fa-hand-holding-dollar", color: "text-yellow-600 bg-yellow-100" },  
        { id: "citytouch", name: { bn: "সিটি টাচ", en: "CityTouch" }, category: "fintech", icon: "fa-solid fa-credit-card", color: "text-indigo-600 bg-indigo-100" },  
        { id: "eblsky", name: "ইবিএল স্কাই", category: "fintech", icon: "fa-solid fa-plane-up", color: "text-sky-600 bg-sky-100" },  
        { id: "bracastha", name: { bn: "ব্র্যাক আস্থা", en: "BRAC Astha" }, category: "fintech", icon: "fa-solid fa-shield-halved", color: "text-blue-700 bg-blue-100" },  
        { id: "nexuspay", name: { bn: "নেক্সাস পে", en: "NexusPay" }, category: "fintech", icon: "fa-solid fa-cash-register", color: "text-amber-600 bg-amber-100" },  
        { id: "okwallet", name: { bn: "ওকে ওয়ালেট", en: "OK Wallet" }, category: "fintech", icon: "fa-solid fa-vault", color: "text-red-600 bg-red-100" },  
        { id: "mcash", name: { bn: "এম ক্যাশ", en: "mCash" }, category: "fintech", icon: "fa-solid fa-coins", color: "text-green-600 bg-green-100" },  
        { id: "payoneer", name: { bn: "পেওনিয়ার", en: "Payoneer" }, category: "fintech", icon: "fa-solid fa-globe", color: "text-red-500 bg-red-100" },  
        { id: "binance", name: { bn: "বাইনান্স", en: "Binance" }, category: "fintech", icon: "fa-solid fa-chart-line", color: "text-yellow-600 bg-yellow-100" },  
        { id: "wise", name: { bn: "ওয়াইজ", en: "Wise" }, category: "fintech", icon: "fa-solid fa-arrow-right-arrow-left", color: "text-cyan-600 bg-cyan-100" },  
        { id: "ismart", name: { bn: "আইস্মার্ট", en: "iSmart" }, category: "fintech", icon: "fa-solid fa-building-ngo", color: "text-emerald-700 bg-emerald-100" },  
        { id: "ucbmbl", name: { bn: "ইউসিবি ব্যাংকিং", en: "UCB Banking" }, category: "fintech", icon: "fa-solid fa-piggy-bank", color: "text-rose-600 bg-rose-100" },  
        { id: "scmobile", name: { bn: "এসসি মোবাইল", en: "SC Mobile" }, category: "fintech", icon: "fa-solid fa-receipt", color: "text-blue-800 bg-blue-100" },  
        { id: "mtbsmart", name: { bn: "এমটিবি স্মার্ট", en: "MTB Smart" }, category: "fintech", icon: "fa-solid fa-network-wired", color: "text-teal-600 bg-teal-100" },  
        { id: "dhakabank", name: { bn: "ঢাকা ব্যাংক গো", en: "Dhaka Bank Go" }, category: "fintech", icon: "fa-solid fa-shield", color: "text-violet-600 bg-violet-100" },  

        // 2. Shopping & E-Commerce  
        { id: "daraz", name: { bn: "দারাজ", en: "Daraz" }, category: "shopping", icon: "fa-solid fa-bag-shopping", color: "text-orange-600 bg-orange-100" },  
        { id: "bikroy", name: { bn: "বিক্রয়.কম", en: "Bikroy.com" }, category: "shopping", icon: "fa-solid fa-store", color: "text-emerald-600 bg-emerald-100" },  
        { id: "chaldal", name: { bn: "চালডাল", en: "Chaldal" }, category: "shopping", icon: "fa-solid fa-cart-shopping", color: "text-yellow-600 bg-yellow-100" },  
        { id: "pickaboo", name: { bn: "পিকাবু", en: "Pickaboo" }, category: "shopping", icon: "fa-solid fa-mobile-button", color: "text-blue-600 bg-blue-100" },  
        { id: "rokomari", name: { bn: "রকমারি", en: "Rokomari" }, category: "shopping", icon: "fa-solid fa-book", color: "text-red-600 bg-red-100" },  
        { id: "startech", name: { bn: "স্টার টেক", en: "Star Tech" }, category: "shopping", icon: "fa-solid fa-laptop", color: "text-rose-600 bg-rose-100" },  
        { id: "ryans", name: { bn: "রায়ান্স", en: "Ryans" }, category: "shopping", icon: "fa-solid fa-desktop", color: "text-blue-700 bg-blue-100" },  
        { id: "aarong", name: { bn: "আড়ং", en: "Aarong" }, category: "shopping", icon: "fa-solid fa-shirt", color: "text-amber-700 bg-amber-100" },  
        { id: "shajgoj", name: { bn: "সাজগোজ", en: "Shajgoj" }, category: "shopping", icon: "fa-solid fa-spa", color: "text-pink-600 bg-pink-100" },  
        { id: "aliexpress", name: { bn: "আলিএক্সপ্রেস", en: "AliExpress" }, category: "shopping", icon: "fa-solid fa-plane", color: "text-red-600 bg-red-100" },  
        { id: "amazon", name: { bn: "অ্যামাজন", en: "Amazon" }, category: "shopping", icon: "fa-brands fa-amazon", color: "text-slate-900 bg-slate-200" },  
        { id: "evaly", name: { bn: "ইভ্যালি", en: "Evaly" }, category: "shopping", icon: "fa-solid fa-tags", color: "text-red-600 bg-red-100" },  
        { id: "othoba", name: { bn: "অথবা", en: "Othoba" }, category: "shopping", icon: "fa-solid fa-basket-shopping", color: "text-blue-600 bg-blue-100" },  
        { id: "priyoshop", name: { bn: "প্রিয়শপ", en: "PriyoShop" }, category: "shopping", icon: "fa-solid fa-boxes-packing", color: "text-cyan-600 bg-cyan-100" },  
        { id: "apex", name: { bn: "অ্যাপেক্স", en: "Apex" }, category: "shopping", icon: "fa-solid fa-shoe-prints", color: "text-indigo-600 bg-indigo-100" },  
        { id: "bata", name: { bn: "বাটা বিডি", en: "Bata BD" }, category: "shopping", icon: "fa-solid fa-socks", color: "text-red-700 bg-red-100" },  
        { id: "sailor", name: { bn: "সেইলর", en: "Sailor" }, category: "shopping", icon: "fa-solid fa-anchor", color: "text-sky-600 bg-sky-100" },  
        { id: "catseye", name: { bn: "ক্যাটস আই", en: "Cats Eye" }, category: "shopping", icon: "fa-solid fa-glasses", color: "text-purple-600 bg-purple-100" },  
        { id: "swap", name: { bn: "সোয়াপ বিডি", en: "SWAP BD" }, category: "shopping", icon: "fa-solid fa-rotate", color: "text-emerald-700 bg-emerald-100" },  
        { id: "jadroo", name: { bn: "যাদরূ", en: "Jadroo" }, category: "shopping", icon: "fa-solid fa-gem", color: "text-yellow-600 bg-yellow-100" },  

        // 3. Logistics & Delivery  
        { id: "pathao", name: { bn: "পাঠাও", en: "Pathao" }, category: "logistics", icon: "fa-solid fa-motorcycle", color: "text-red-600 bg-red-100" },  
        { id: "uber", name: { bn: "উবার", en: "Uber" }, category: "logistics", icon: "fa-brands fa-uber", color: "text-slate-900 bg-slate-200" },  
        { id: "indrive", name: { bn: "ইনড্রাইভ", en: "InDrive" }, category: "logistics", icon: "fa-solid fa-car", color: "text-green-600 bg-green-100" },  
        { id: "foodpanda", name: { bn: "ফুডপান্ডা", en: "Foodpanda" }, category: "logistics", icon: "fa-solid fa-utensils", color: "text-pink-600 bg-pink-100" },  
        { id: "redx", name: { bn: "রেডএক্স", en: "RedX" }, category: "logistics", icon: "fa-solid fa-box", color: "text-red-700 bg-red-100" },  
        { id: "steadfast", name: { bn: "স্টেডফাস্ট", en: "Steadfast" }, category: "logistics", icon: "fa-solid fa-truck-fast", color: "text-blue-600 bg-blue-100" },  
        { id: "shohoz", name: { bn: "সহজ", en: "Shohoz" }, category: "logistics", icon: "fa-solid fa-bus", color: "text-emerald-600 bg-emerald-100" },  
        { id: "paperfly", name: { bn: "পেপারফ্লাই", en: "Paperfly" }, category: "logistics", icon: "fa-solid fa-paper-plane", color: "text-sky-600 bg-sky-100" },  
        { id: "ecourier", name: { bn: "ই-কুরিয়ার", en: "eCourier" }, category: "logistics", icon: "fa-solid fa-envelope", color: "text-orange-600 bg-orange-100" },  
        { id: "sundarban", name: { bn: "সুন্দরবন কুরিয়ার", en: "Sundarban" }, category: "logistics", icon: "fa-solid fa-truck-ramp-box", color: "text-yellow-600 bg-yellow-100" },  
        { id: "saparibahan", name: { bn: "এস এ পরিবহন", en: "SA Paribahan" }, category: "logistics", icon: "fa-solid fa-dolly", color: "text-indigo-600 bg-indigo-100" },  
        { id: "obhai", name: { bn: "ওভাই", en: "Obhai" }, category: "logistics", icon: "fa-solid fa-taxi", color: "text-lime-600 bg-lime-100" },  
        { id: "klavio", name: { bn: "ক্লাভিও", en: "Klavio" }, category: "logistics", icon: "fa-solid fa-dolly-flatbed", color: "text-purple-600 bg-purple-100" },  
        { id: "railsheba", name: { bn: "রেল সেবা", en: "Rail Sheba" }, category: "logistics", icon: "fa-solid fa-train", color: "text-emerald-800 bg-emerald-100" },  
        { id: "busbd", name: { bn: "বিডি বাস টিকিট", en: "BD Bus Ticket" }, category: "logistics", icon: "fa-solid fa-ticket", color: "text-blue-700 bg-blue-100" },  
        { id: "jatri", name: { bn: "যাত্রী", en: "Jatri" }, category: "logistics", icon: "fa-solid fa-route", color: "text-red-500 bg-red-100" },  
        { id: "hungrynaki", name: { bn: "হাংরিনাকি", en: "HungryNaki" }, category: "logistics", icon: "fa-solid fa-bowl-food", color: "text-amber-600 bg-amber-100" },  
        { id: "dominos", name: { bn: "ডমিনোজ পিজ্জা", en: "Domino's Pizza" }, category: "logistics", icon: "fa-solid fa-pizza-slice", color: "text-blue-600 bg-blue-100" },  
        { id: "kfcbd", name: { bn: "কেএফসি বিডি", en: "KFC BD" }, category: "logistics", icon: "fa-solid fa-drumstick-bite", color: "text-red-700 bg-red-100" },  
        { id: "sharetrip", name: { bn: "শেয়ারট্রিপ", en: "ShareTrip" }, category: "logistics", icon: "fa-solid fa-plane-departure", color: "text-cyan-600 bg-cyan-100" },  

        // 4. Social & Messaging  
        { id: "facebook", name: { bn: "ফেসবুক", en: "Facebook" }, category: "social", icon: "fa-brands fa-facebook", color: "text-blue-600 bg-blue-100" },  
        { id: "messenger", name: { bn: "মেসেঞ্জার", en: "Messenger" }, category: "social", icon: "fa-brands fa-facebook-messenger", color: "text-cyan-600 bg-cyan-100" },  
        { id: "whatsapp", name: { bn: "হোয়াটসঅ্যাপ", en: "WhatsApp" }, category: "social", icon: "fa-brands fa-whatsapp", color: "text-emerald-600 bg-emerald-100" },  
        { id: "youtube", name: { bn: "ইউটিউব", en: "YouTube" }, category: "social", icon: "fa-brands fa-youtube", color: "text-red-600 bg-red-100" },  
        { id: "instagram", name: { bn: "ইনস্টাগ্রাম", en: "Instagram" }, category: "social", icon: "fa-brands fa-instagram", color: "text-pink-600 bg-pink-100" },  
        { id: "tiktok", name: { bn: "টিকটক", en: "TikTok" }, category: "social", icon: "fa-brands fa-tiktok", color: "text-slate-900 bg-slate-200" },  
        { id: "telegram", name: { bn: "টেলিগ্রাম", en: "Telegram" }, category: "social", icon: "fa-brands fa-telegram", color: "text-sky-600 bg-sky-100" },  
        { id: "imo", name: { bn: "ইমো", en: "Imo" }, category: "social", icon: "fa-solid fa-comment-dots", color: "text-blue-500 bg-blue-100" },  
        { id: "linkedin", name: { bn: "লিংকডইন", en: "LinkedIn" }, category: "social", icon: "fa-brands fa-linkedin", color: "text-blue-700 bg-blue-100" },  
        { id: "twitter", name: { bn: "এক্স (টুইটার)", en: "X (Twitter)" }, category: "social", icon: "fa-brands fa-x-twitter", color: "text-slate-900 bg-slate-200" },  
        { id: "snapchat", name: { bn: "স্ন্যাপচ্যাট", en: "Snapchat" }, category: "social", icon: "fa-brands fa-snapchat", color: "text-yellow-500 bg-yellow-100" },  
        { id: "pinterest", name: { bn: "পিন্টারেস্ট", en: "Pinterest" }, category: "social", icon: "fa-brands fa-pinterest", color: "text-red-600 bg-red-100" },  
        { id: "viber", name: { bn: "ভাইবার", en: "Viber" }, category: "social", icon: "fa-brands fa-viber", color: "text-purple-600 bg-purple-100" },  
        { id: "discord", name: { bn: "ডিসকর্ড", en: "Discord" }, category: "social", icon: "fa-brands fa-discord", color: "text-indigo-600 bg-indigo-100" },  
        { id: "reddit", name: { bn: "রেডিট", en: "Reddit" }, category: "social", icon: "fa-brands fa-reddit", color: "text-orange-600 bg-orange-100" },  
        { id: "quora", name: { bn: "কোয়োরা", en: "Quora" }, category: "social", icon: "fa-brands fa-quora", color: "text-red-700 bg-red-100" },  
        { id: "medium", name: { bn: "মিডিয়াম", en: "Medium" }, category: "social", icon: "fa-brands fa-medium", color: "text-slate-900 bg-slate-200" },  
        { id: "threads", name: { bn: "থ্রেডস", en: "Threads" }, category: "social", icon: "fa-solid fa-at", color: "text-slate-800 bg-slate-200" },  
        { id: "skype", name: { bn: "স্কাইপ", en: "Skype" }, category: "social", icon: "fa-brands fa-skype", color: "text-sky-500 bg-sky-100" },  
        { id: "likee", name: { bn: "লাইকি", en: "Likee" }, category: "social", icon: "fa-solid fa-heart", color: "text-rose-500 bg-rose-100" },  

        // 5. AI & Productivity  
        { id: "chatgpt", name: { bn: "চ্যাটজিপিটি", en: "ChatGPT" }, category: "ai", icon: "fa-solid fa-robot", color: "text-emerald-700 bg-emerald-100" },  
        { id: "gemini", name: { bn: "জেমিনি এআই", en: "Google Gemini" }, category: "ai", icon: "fa-solid fa-sparkles", color: "text-blue-600 bg-blue-100" },  
        { id: "midjourney", name: { bn: "মিডজার্নি", en: "Midjourney" }, category: "ai", icon: "fa-solid fa-wand-magic-sparkles", color: "text-indigo-600 bg-indigo-100" },  
        { id: "claude", name: { bn: "ক্লড এআই", en: "Claude AI" }, category: "ai", icon: "fa-solid fa-brain", color: "text-amber-700 bg-amber-100" },  
        { id: "suno", name: { bn: "সুনো এআই", en: "Suno AI" }, category: "ai", icon: "fa-solid fa-music", color: "text-purple-600 bg-purple-100" },  
        { id: "canva", name: { bn: "ক্যানভা", en: "Canva" }, category: "ai", icon: "fa-solid fa-palette", color: "text-cyan-600 bg-cyan-100" },  
        { id: "copilot", name: { bn: "কপাইলট", en: "MS Copilot" }, category: "ai", icon: "fa-brands fa-microsoft", color: "text-blue-600 bg-blue-100" },  
        { id: "runway", name: { bn: "রানওয়ে", en: "Runway" }, category: "ai", icon: "fa-solid fa-video", color: "text-red-600 bg-red-100" },  
        { id: "elevenlabs", name: { bn: "ইলেভেনল্যাবস", en: "ElevenLabs" }, category: "ai", icon: "fa-solid fa-microphone-lines", color: "text-slate-800 bg-slate-200" },  
        { id: "grammarly", name: { bn: "গ্রামারলি", en: "Grammarly" }, category: "ai", icon: "fa-solid fa-spell-check", color: "text-emerald-600 bg-emerald-100" },  
        { id: "quillbot", name: { bn: "কুইলবট", en: "QuillBot" }, category: "ai", icon: "fa-solid fa-feather-pointed", color: "text-green-600 bg-green-100" },  
        { id: "capcut", name: { bn: "ক্যাপকাট", en: "CapCut" }, category: "ai", icon: "fa-solid fa-scissors", color: "text-slate-900 bg-slate-200" },  
        { id: "photoshop", name: { bn: "ফটোশপ এআই", en: "Photoshop AI" }, category: "ai", icon: "fa-solid fa-image", color: "text-blue-800 bg-blue-100" },  
        { id: "notionai", name: { bn: "নোশন এআই", en: "Notion AI" }, category: "ai", icon: "fa-solid fa-file-lines", color: "text-slate-900 bg-slate-200" },  
        { id: "perplexity", name: { bn: "পারপ্লেক্সিটি", en: "Perplexity" }, category: "ai", icon: "fa-solid fa-compass", color: "text-teal-600 bg-teal-100" },  
        { id: "leonardo", name: { bn: "লিওনার্দো এআই", en: "Leonardo AI" }, category: "ai", icon: "fa-solid fa-paintbrush", color: "text-pink-600 bg-pink-100" },  
        { id: "pika", name: { bn: "পিকা এআই", en: "Pika AI" }, category: "ai", icon: "fa-solid fa-film", color: "text-amber-600 bg-amber-100" },  
        { id: "remini", name: { bn: "রিমিনি", en: "Remini" }, category: "ai", icon: "fa-solid fa-face-smile", color: "text-red-500 bg-red-100" },  
        { id: "deepl", name: { bn: "ডিপএল", en: "DeepL" }, category: "ai", icon: "fa-solid fa-language", color: "text-blue-700 bg-blue-100" },  
        { id: "veedio", name: { bn: "ভিড আইও", en: "VEED.io" }, category: "ai", icon: "fa-solid fa-clackboard", color: "text-violet-600 bg-violet-100" },  

        // 6. Gaming  
        { id: "pubg", name: { bn: "পাবজি মোবাইল", en: "PUBG Mobile" }, category: "gaming", icon: "fa-solid fa-crosshairs", color: "text-amber-700 bg-amber-100" },  
        { id: "freefire", name: { bn: "ফ্রি ফায়ার", en: "Free Fire" }, category: "gaming", icon: "fa-solid fa-fire", color: "text-orange-600 bg-orange-100" },  
        { id: "ludo", name: { bn: "লুডো কিং", en: "Ludo King" }, category: "gaming", icon: "fa-solid fa-dice", color: "text-red-600 bg-red-100" },  
        { id: "cod", name: { bn: "কল অব ডিউটি", en: "Call of Duty" }, category: "gaming", icon: "fa-solid fa-person-rifle", color: "text-slate-900 bg-slate-200" },  
        { id: "coc", name: { bn: "ক্ল্যাশ অব ক্ল্যানস", en: "Clash of Clans" }, category: "gaming", icon: "fa-solid fa-shield-cat", color: "text-yellow-600 bg-yellow-100" },  
        { id: "candycrush", name: { bn: "ক্যান্ডি ক্রাশ", en: "Candy Crush" }, category: "gaming", icon: "fa-solid fa-candy-cane", color: "text-pink-600 bg-pink-100" },  
        { id: "subway", name: { bn: "সাবওয়ে সার্ফার্স", en: "Subway Surfers" }, category: "gaming", icon: "fa-solid fa-person-running", color: "text-emerald-600 bg-emerald-100" },  
        { id: "roblox", name: { bn: "রোবলক্স", en: "Roblox" }, category: "gaming", icon: "fa-solid fa-cube", color: "text-red-600 bg-red-100" },  
        { id: "minecraft", name: { bn: "মাইনক্রাফট", en: "Minecraft" }, category: "gaming", icon: "fa-solid fa-cubes", color: "text-green-700 bg-green-100" },  
        { id: "asphalt9", name: { bn: "এসফাল্ট ৯", en: "Asphalt 9" }, category: "gaming", icon: "fa-solid fa-gauge-high", color: "text-blue-600 bg-blue-100" },  
        { id: "fifa", name: { bn: "ইএ স্পোর্টস এফসি", en: "EA Sports FC" }, category: "gaming", icon: "fa-solid fa-football", color: "text-emerald-800 bg-emerald-100" },  
        { id: "mlbb", name: { bn: "মোবাইল লেজেন্ডস", en: "Mobile Legends" }, category: "gaming", icon: "fa-solid fa-khanda", color: "text-indigo-600 bg-indigo-100" },  
        { id: "pool8", name: { bn: "৮ বল পুল", en: "8 Ball Pool" }, category: "gaming", icon: "fa-solid fa-circle-dot", color: "text-blue-800 bg-blue-100" },  
        { id: "templerun", name: { bn: "টেম্পল রান", en: "Temple Run" }, category: "gaming", icon: "fa-solid fa-skull", color: "text-amber-800 bg-amber-100" },  
        { id: "shadowfight", name: { bn: "শ্যাডো ফাইট", en: "Shadow Fight" }, category: "gaming", icon: "fa-solid fa-user-ninja", color: "text-slate-800 bg-slate-200" },  
        { id: "hillclimb", name: { bn: "হিল ক্লাইম", en: "Hill Climb" }, category: "gaming", icon: "fa-solid fa-truck-monster", color: "text-red-500 bg-red-100" },  
        { id: "chesscom", name: { bn: "চেস.কম", en: "Chess.com" }, category: "gaming", icon: "fa-solid fa-chess-knight", color: "text-green-800 bg-green-100" },  
        { id: "carrompool", name: { bn: "ক্যারম পুল", category: "gaming", icon: "fa-solid fa-bullseye", color: "text-amber-600 bg-amber-100" },  
        { id: "efootball", name: { bn: "ইফুটবল পেস", en: "eFootball" }, category: "gaming", icon: "fa-solid fa-award", color: "text-blue-600 bg-blue-100" },  
        { id: "clashroyale", name: { bn: "ক্ল্যাশ রয়্যাল", en: "Clash Royale" }, category: "gaming", icon: "fa-solid fa-crown", color: "text-yellow-500 bg-yellow-100" }  
    ];  

    const categoryNames = {  
        fintech: { bn: "মোবাইল ব্যাংকিং ও ফিনটেক (MFS)", en: "FinTech & Banking" },  
        shopping: { bn: "ই-কমার্স ও অনলাইন শপিং", en: "Shopping & E-Commerce" },  
        logistics: { bn: "রাইড, ফুড ও কুরিয়ার ডেলিভারি", en: "Logistics & Delivery" },  
        social: { bn: "সোশ্যাল মিডিয়া ও মেসেজিং", en: "Social & Messaging" },  
        ai: { bn: "এআই ও ক্রিয়েটিভ টুলস", en: "AI & Productivity" },  
        gaming: { bn: "পপুলার গেমস", en: "Gaming" }  
    };  

    const uiTexts = {  
        bn: {  
            navTitle: "আমার ডিজিটাল বাংলাদেশ",  
            navSub: "Digital Bangladesh",  
            langBtn: "English",  
            heroBadge: "⚡ ডিজিটাল বাংলাদেশ অ্যাপস ট্র্যাকার (১০০+ অ্যাপস)",  
            heroTitle: "আপনি ডিজিটাল দুনিয়ায় কত পার্সেন্ট আছেন?",  
            heroDesc: "নিচের প্রতিটি ক্যাটাগরি থেকে আপনার ব্যবহৃত অ্যাপসগুলোতে টিক দিন এবং নিচে আপনার নাম ও গোল সুন্দর ছবি আপলোড করে কাস্টম পোস্টার তৈরি করুন।",  
            scoreLabel: "লাইভ এডাপশন স্কোর",  
            searchPlaceholder: "অ্যাপের নাম দিয়ে খুঁজুন...",  
            selectAll: "সব সিলেক্ট করুন",  
            reset: "রিসেট করুন",  
            cardMakerTitle: "কাস্টমাইজড প্রোফাইল ও গোল ফটো কার্ড মেকার",  
            cardMakerDesc: "আপনার নাম লিখুন এবং ছবি আপলোড করুন (ছবিটি কার্ডে সুন্দর গোলাকার ফ্রেমের মধ্যে থাকবে)",  
            labelName: "আপনার নাম (কার্ডে দেখাবে)",  
            labelPhoto: "আপনার সুন্দর ছবি আপলোড করুন",  
            generateBtn: "পোস্ট ফটো কার্ড তৈরি করুন",  
            modalTitle: "আপনার কাস্টম ডিজিটাল ফটো কার্ড",  
            canvasTitle: "আমার ডিজিটাল বাংলাদেশ",  
            canvasSub: "Digital Bangladesh",  
            canvasBadge: "🇧🇩 ডিজিটাল নাগরিক",  
            canvasScoreLabel: "ডিজিটাল এ্যাডাপশন স্কোর:",  
            downloadBtn: "এইচডি ফটো ডাউনলোড করুন (PNG)",  
            closeBtn: "বন্ধ করুন",  
            contactHeading: "আমাদের সাথে যোগাযোগ করুন",  
            contactSub: "নতুন অ্যাপ যুক্ত করা বা যেকোনো প্রশ্নের জন্য ইমেইল পাঠান।",  
            formName: "আপনার নাম",  
            formEmail: "আপনার ইমেইল",  
            formMsg: "বার্তা বা পরামর্শ",  
            formSend: "বার্তা পাঠান (Formspree)",  
            footerCopy: "© 2026 Digital Bangladesh. All Rights Reserved."  
        },  
        en: {  
            navTitle: "Digital Bangladesh",  
            navSub: "Digital Bangladesh Tracker",  
            langBtn: "বাংলা",  
            heroBadge: "⚡ Digital Bangladesh Apps Tracker (100+ Apps)",  
            heroTitle: "What percentage of the digital world are you in?",  
            heroDesc: "Select the apps you use from each category below, upload your name and photo, and generate your custom poster.",  
            scoreLabel: "Live Adoption Score",  
            searchPlaceholder: "Search app name...",  
            selectAll: "Select All",  
            reset: "Reset",  
            cardMakerTitle: "Custom Profile & Circular Photo Card Maker",  
            cardMakerDesc: "Enter your name and upload your photo (will be framed inside a circle on the card)",  
            labelName: "Your Name (Shown on Card)",  
            labelPhoto: "Upload Your Photo",  
            generateBtn: "Generate Poster Photo Card",  
            modalTitle: "Your Custom Digital Photo Card",  
            canvasTitle: "Digital Bangladesh",  
            canvasSub: "Digital Footprint Tracker",  
            canvasBadge: "🇧🇩 Digital Citizen",  
            canvasScoreLabel: "Digital Adoption Score:",  
            downloadBtn: "Download HD Photo (PNG)",  
            closeBtn: "Close",  
            contactHeading: "Contact Us",  
            contactSub: "Send an email for adding new apps or any inquiries.",  
            formName: "Your Name",  
            formEmail: "Your Email",  
            formMsg: "Message or Feedback",  
            formSend: "Send Message (Formspree)",  
            footerCopy: "© 2026 Digital Bangladesh. All Rights Reserved."  
        }  
    };  

    let currentLang = 'bn';  
    let uploadedPhotoUrl = 'https://images.unsplash.com/photo-1534528741775-53994a69daeb?w=200';  

    window.addEventListener('DOMContentLoaded', () => {  
        renderCategories();  
        loadUserData();  

        document.getElementById('inputUserPhoto').addEventListener('change', function(e) {  
            const file = e.target.files[0];  
            if (file) {  
                const reader = new FileReader();  
                reader.onload = function(evt) {  
                    uploadedPhotoUrl = evt.target.result;  
                    saveUserData();  
                };  
                reader.readAsDataURL(file);  
            }  
        });  
    });  

    function renderCategories() {  
        const container = document.getElementById('appsCategoriesContainer');  
        container.innerHTML = '';  

        Object.keys(categoryNames).forEach(cat => {  
            const catApps = appDatabase.filter(app => app.category === cat);  
            if (catApps.length === 0) return;  

            const catBox = document.createElement('div');  
            catBox.className = "glass-card p-4 sm:p-5 rounded-3xl space-y-3";  
            catBox.innerHTML = `  
                <h3 class="text-sm font-black text-black border-b border-slate-200 pb-2 flex items-center justify-between">  
                    <span>${categoryNames[cat][currentLang]}</span>  
                    <span class="text-[11px] bg-emerald-100 text-black px-2.5 py-0.5 rounded-full font-bold border border-emerald-300">${catApps.length} Apps</span>  
                </h3>  
                <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-2.5">  
                    ${catApps.map(app => `  
                        <label class="cursor-pointer relative group">  
                            <input type="checkbox" value="${app.id}" onchange="updateScore(); saveUserData();" class="app-checkbox hidden">  
                            <div class="app-card rounded-xl flex items-center space-x-2 relative">  
                                <div class="w-7 h-7 rounded-lg ${app.color} flex items-center justify-center text-xs flex-shrink-0 shadow-sm border border-slate-200">  
                                    <i class="${app.icon}"></i>  
                                </div>  
                                <span class="text-[11px] font-black text-black truncate">${app.name[currentLang]}</span>  
                                <div class="check-badge hidden absolute -top-1 -right-1 w-4 h-4 bg-emerald-600 text-white rounded-full items-center justify-center text-[9px] shadow-md border border-white">  
                                    <i class="fa-solid fa-check"></i>  
                                </div>  
                            </div>  
                        </label>  
                    `).join('')}  
                </div>  
            `;  
            container.appendChild(catBox);  
        });  
    }  

    function updateScore() {  
        const selectedApps = document.querySelectorAll('.app-checkbox:checked');  
        const percent = Math.min(100, Math.round((selectedApps.length / appDatabase.length) * 100));  

        document.getElementById('heroLiveScore').innerText = percent + '%';  
        document.getElementById('heroScoreBar').style.width = percent + '%';  
    }  

    function selectAllApps(status) {  
        document.querySelectorAll('.app-checkbox').forEach(cb => cb.checked = status);  
        updateScore();  
        saveUserData();  
    }  

    function filterApps() {  
        const query = document.getElementById('appSearchInput').value.toLowerCase();  
        document.querySelectorAll('.app-card').forEach(card => {  
            const name = card.querySelector('span').innerText.toLowerCase();  
            card.parentElement.style.display = name.includes(query) ? 'block' : 'none';  
        });  
    }  

    function saveUserData() {  
        const userName = document.getElementById('inputUserName').value;  
        const selectedApps = Array.from(document.querySelectorAll('.app-checkbox:checked')).map(cb => cb.value);  
          
        localStorage.setItem('df_userName', userName);  
        localStorage.setItem('df_selectedApps', JSON.stringify(selectedApps));  
        if (uploadedPhotoUrl.startsWith('data:image')) {  
            localStorage.setItem('df_photoUrl', uploadedPhotoUrl);  
        }  
    }  

    function loadUserData() {  
        const savedName = localStorage.getItem('df_userName');  
        const savedApps = JSON.parse(localStorage.getItem('df_selectedApps') || '[]');  
        const savedPhoto = localStorage.getItem('df_photoUrl');  

        if (savedName) document.getElementById('inputUserName').value = savedName;  
        if (savedPhoto) uploadedPhotoUrl = savedPhoto;  

        if (savedApps.length > 0) {  
            document.querySelectorAll('.app-checkbox').forEach(cb => {  
                if (savedApps.includes(cb.value)) cb.checked = true;  
            });  
            updateScore();  
        }  
    }  

    function generatePhotoCard() {  
        const selectedApps = Array.from(document.querySelectorAll('.app-checkbox:checked')).map(cb => cb.value);  
        if (selectedApps.length === 0) {  
            alert(currentLang === 'bn' ? "দয়া করে অন্তত ১টি অ্যাপ সিলেক্ট করুন!" : "Please select at least 1 app!");  
            return;  
        }  

        const userName = document.getElementById('inputUserName').value.trim() || (currentLang === 'bn' ? "সাকিব হাসান" : "Shakib Hasan");  
        const percent = Math.min(100, Math.round((selectedApps.length / appDatabase.length) * 100));  

        document.getElementById('cardUserNameText').innerText = userName;  
        document.getElementById('cardUserProfileImg').src = uploadedPhotoUrl;  
        document.getElementById('cardScorePercent').innerText = percent + '%';  

        document.getElementById('cardPreviewModal').classList.remove('hidden');  
    }  

    function closeModal() {  
        document.getElementById('cardPreviewModal').classList.add('hidden');  
    }  

    function downloadCardImage() {  
        const canvasCard = document.getElementById('facebookCardCanvas');  
        html2canvas(canvasCard, { scale: 2, useCORS: true }).then(canvas => {  
            const link = document.createElement('a');  
            link.download = 'digital-bangladesh-card.png';  
            link.href = canvas.toDataURL('image/png');  
            link.click();  
        });  
    }  

    function toggleLanguage() {  
        currentLang = currentLang === 'bn' ? 'en' : 'bn';  
        const t = uiTexts[currentLang];  

        // Update UI elements dynamically based on language  
        document.getElementById('navTitle').innerText = t.navTitle;  
        document.getElementById('navSubtitle').innerText = t.navSub;  
        document.getElementById('langToggleBtn').innerHTML = `<i class="fa-solid fa-language mr-1"></i> ${t.langBtn}`;  
        document.getElementById('heroBadge').innerText = t.heroBadge;  
        document.getElementById('heroTitle').innerText = t.heroTitle;  
        document.getElementById('heroDesc').innerText = t.heroDesc;  
        document.getElementById('scoreLabel').innerText = t.scoreLabel;  
        document.getElementById('appSearchInput').placeholder = t.searchPlaceholder;  
        document.getElementById('selectAllBtn').innerText = t.selectAll;  
        document.getElementById('resetBtn').innerText = t.reset;  
        document.getElementById('cardMakerTitle').innerHTML = `<i class="fa-solid fa-id-card text-emerald-600"></i> ${t.cardMakerTitle}`;  
        document.getElementById('cardMakerDesc').innerText = t.cardMakerDesc;  
        document.getElementById('labelName').innerText = t.labelName;  
        document.getElementById('labelPhoto').innerText = t.labelPhoto;  
        document.getElementById('generateBtn').innerHTML = `<i class="fa-solid fa-wand-magic-sparkles mr-2"></i> ${t.generateBtn}`;  
        document.getElementById('modalHeaderTitle').innerText = t.modalTitle;  
        document.getElementById('canvasTitle').innerText = t.canvasTitle;  
        document.getElementById('canvasSubtitle').innerText = t.canvasSub;  
        document.getElementById('canvasBadgeText').innerText = t.canvasBadge;  
        document.getElementById('canvasScoreLabel').innerText = t.canvasScoreLabel;  
        document.getElementById('downloadBtn').innerHTML = `<i class="fa-solid fa-download mr-1.5"></i> ${t.downloadBtn}`;  
        document.getElementById('closeModalBtn').innerText = t.closeBtn;  
        document.getElementById('contactHeading').innerText = t.contactHeading;  
        document.getElementById('contactSub').innerText = t.contactSub;  
        document.getElementById('formNameLabel').innerText = t.formName;  
        document.getElementById('formEmailLabel').innerText = t.formEmail;  
        document.getElementById('formMsgLabel').innerText = t.formMsg;  
        document.getElementById('formSubmitBtn').innerHTML = `<i class="fa-solid fa-paper-plane mr-1.5"></i> ${t.formSend}`;  
        document.getElementById('footerCopy').innerText = t.footerCopy;  

        renderCategories();  
        loadUserData();  
    }  
</script>

</body>  
</html>এটা ফাইল আকারে দাও যাতে ডাউনলোড করতে পারি
