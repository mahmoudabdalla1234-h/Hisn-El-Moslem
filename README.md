<!DOCTYPE html>

<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>حصن المسلم</title>
<script src="https://cdn.tailwindcss.com"></script>
<link href="https://fonts.googleapis.com/css2?family=Amiri&family=Tajawal:wght@400;700&display=swap" rel="stylesheet">
<style>
body { font-family: 'Tajawal', sans-serif; background-color: #f8fafc; }
.font-amiri { font-family: 'Amiri', serif; }
.active-tab { color: #15803d; border-top: 3px solid #15803d; }
</style>
</head>
<body class="pb-20">

<header class="bg-green-700 text-white p-5 text-center shadow-md">
    <h1 class="text-2xl font-bold font-amiri">حصن المسلم</h1>
</header>

<div id="app" class="max-w-md mx-auto p-4">
    <!-- المحتوى يتغير بواسطة الجافاسكريبت -->
</div>

<nav class="fixed bottom-0 left-0 right-0 bg-white shadow-lg border-t flex justify-around p-2">
    <button onclick="render('azkar')" class="flex flex-col items-center p-2"><span>🌙</span><small>الأذكار</small></button>
    <button onclick="render('sebha')" class="flex flex-col items-center p-2"><span>📿</span><small>السبحة</small></button>
    <button onclick="render('quran')" class="flex flex-col items-center p-2"><span>📖</span><small>المصحف</small></button>
</nav>

<script>
    let counter = 0;
    function render(page) {
        const container = document.getElementById('app');
        if(page === 'azkar') {
            container.innerHTML = `
                <div class="bg-white p-4 rounded-xl shadow mb-4 border-r-4 border-green-600">
                    <p class="font-amiri text-xl leading-relaxed">أَصْبَحْنَا وَأَصْبَحَ المُلْكُ لِلَّهِ وَالْحَمْدُ لِلَّهِ، لَا إِلَهَ إِلَّا اللَّهُ وَحْدَهُ لَا شَرِيكَ لَهُ</p>
                </div>
                <div class="bg-white p-4 rounded-xl shadow border-r-4 border-green-600">
                    <p class="font-amiri text-xl leading-relaxed">اللّهُ لاَ إِلَـهَ إِلاَّ هُوَ الْحَيُّ الْقَيُّومُ لاَ تَأْخُذُهُ سِنَةٌ وَلاَ نَوْمٌ</p>
                </div>`;
        } else if(page === 'sebha') {
            container.innerHTML = `
                <div class="text-center py-10">
                    <div onclick="counter++; render('sebha')" class="w-40 h-40 bg-green-600 text-white rounded-full mx-auto flex items-center justify-center text-5xl shadow-xl active:scale-90 transition-transform cursor-pointer">${counter}</div>
                    <button onclick="counter=0; render('sebha')" class="mt-5 text-gray-500 underline">تصفير العداد</button>
                </div>`;
        } else {
            container.innerHTML = `<div class="text-center p-10 bg-white rounded-xl shadow"><p>قريباً: المصحف كاملاً للقراءة والاستماع</p></div>`;
        }
    }
    window.onload = () => render('azkar');
</script>
</body>
</html>
