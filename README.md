<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>معاني الأسماء</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; margin: 50px; background-color: #f9f9f9; }
        h1 { color: #5a3e2b; }
        .header-img { width: 100%; height: auto; }
        marquee { font-size: 24px; font-weight: bold; color: #007b5e; }
        input, button { margin: 10px; padding: 10px; font-size: 16px; }
        #result { margin-top: 20px; font-size: 20px; color: #007b5e; }
        .footer { display: flex; justify-content: space-between; padding: 20px; }
        #date { font-size: 18px; }
        .visitor-count { font-size: 18px; }
        audio { display: none; }
    </style>
</head>
<body>

    <img src="https://h.top4top.io/p_3273fliay1.png" alt="الشعار" class="header-img">
    <marquee direction="right">اللغة العربية ليست مجرد وسيلة للتواصل، بل هي رمز الهوية وثقافة الأمة.</marquee>

    <h1>اكتشف معنى اسمك</h1>
    <p>أدخل اسمك ليظهر لك معناه</p>
    <input type="text" id="nameInput" placeholder="أدخل الاسم هنا">
    <button onclick="showMeaning()">اعرض المعنى</button>
    <div id="result"></div>

    <!-- زر التعرف على الاسم بالخط المسند -->
    <button onclick="openCalligraphySite()">تعرف على اسمك بالخط المسند</button>

    <div class="footer">
        <div id="date">18 ديسمبر 2024 م</div>
        <div class="visitor-count">عدد الزوار: <span id="visitorCount">0</span></div>
        <div id="manager" style="float: left;">إدارة المدرسة: أ. زهرة الكاظم</div>
        <div id="alcso" style="float: right;">لجنة الألكسو واليونسكو: أ. أمل ربيع</div>
    </div>

    <audio id="backgroundAudio" autoplay loop>
        <source src="https://www.dropbox.com/scl/fi/ic0q74yk2idovmezz5jzt/2017.mp3?rlkey=y5y028qaln2b0w8f5kq4fzsq4&st=whmdpa24&dl=1" type="audio/mpeg">
    </audio>

    <script>
        let visitorCount = 0;

        function showMeaning() {
            const name = document.getElementById('nameInput').value.trim();
            const meanings = {
                "مريم": "اسم عربي ويعني السيدة الطاهرة.",
                "زهرة": "النبتة الجميلة الملونة.",
                "نورة": "من النور، أي الضوء.",
                "إيمان": "الصدق والتصديق والإيمان بالله.",
                "نرجس": "نوع من الأزهار الجميلة.",
                "خديجة": "الطفلة التي ولدت قبل موعدها.",
                "منى": "الآمال والطموحات.",
                "مكي": "من مكة المكرمة.",
                "معصومة": "المطهرة والمبرأة من الأخطاء.",
                "زهراء": "المضيئة والمشرقة.",
                "بتول": "الفتاة العذراء المكرمة.",
                "زهير": "الشجاع الذي لا يهاب.",
                "لطيفة": "اللطيفة الهادئة والطيبة.",
                "خليفة": "الذي يخلف الآخرين أو المسؤول.",
                "شيخة": "امرأة ذات مكانة عالية.",
                "مروة": "الحجارة البيضاء الجميلة.",
                "دعاء": "التمني والدعوة للأشياء الجميلة.",
                "ليلى": "اسم عربي ويعني الظلام أو الليل.",
                "رباب": "اسم عربي قديم معناه السحاب الأبيض.",
                "عباس": "اسم عربي يعني الأسد أو القوي الشجاع.",
                "سامية": "الرفيعة والمقام العالي.",
                "أمينة": "التي يمكن الوثوق بها.",
                "أماني": "الآمال والطموحات.",
                "سمية": "المرأة الرفيعة الطيبة.",
                "أسماء": "التي لها أسماء عظيمة أو مكانة مرموقة.",
                "حيدر": "اسم عربي يعني الأسد أو الشخص القوي الشجاع.",
                "حلا": "اسم عربي يعبر عن الجمال والنعومة، ويدل على السهولة والجاذبية.",
                "وديع": "الشخص الهادئ الذي يتمتع برقة القلب واللطافة.",
                "نور": "الضوء أو الإشراق، ويعني اللمعان الذي يضيء المكان.",
                "نورة": "اسم عربي مشتق من 'النور'، ويعني الضياء أو النور الساطع.",
                "جهاد": "النضال والكفاح في سبيل الحق.",
                "سعاد": "السعادة والسرور.",
                "شفيقة": "الرقيقة الطيبة التي تشعر بالآخرين.",
                "ابتسام": "الابتسامة التي تعكس الفرح والتفاؤل.",
                "حميدة": "التي تتمتع بالصفات الطيبة والمحمودة.",
                "رقية": "الرفعة والعلو، أو الدعاء بالشفاء.",
                "طيبة": "التي تتمتع بالرقة والنعومة والود.",
                "فاطمة": "التي تفطم أو تترك شيئًا.",
                "صلاح": "الاستقامة والإصلاح.",
                "خولة": "اسم عربي يعني الفتاة الجميلة أو الظبية.",
                "دانة": "اللؤلؤة الثمينة.",
                "درة": "اللؤلؤة، أو الشيء النفيس.",
                "حور": "العيون الواسعة السوداء الجميلة، أو الجمال البراق.",
                "كريمة": "التي تتمتع بالكرم والجود.",
                "زمزم": "اسم بئر في مكة المكرمة، ويعني الماء العذب.",
                "علي": "الرفيع أو المرتفع، أو العالي الشأن.",
                "عباس": "الأسد أو القوي الشجاع.",
                "كرار": "الذي يهاجم بشجاعة، ويعود للتكرار.",
                "محسن": "الذي يحسن ويقدم الخير.",
                "راشد": "الذي يسير في الطريق الصحيح.",
                "جليل": "العظيم والموقر.",
                "محمد": "المحمود، أو صاحب الخصال الحميدة.",
                "قاسم": "الموزع أو الذي يشارك في توزيع الأشياء.",
                "كاظم": "الذي يكظم غيظه أو يعفو عن الآخرين.",
                "ابراهيم": "أبو الأنبياء، ويعني الأب الجدير بالاحترام.",
                "جميل": "الذي يتمتع بالجمال الجسدي والروحي.",
                "جميلة": "التي تتمتع بالجمال والأناقة.",
                "عقيل": "الذكي العاقل الذي يتصرف بحكمة.",
                "حر": "الشخص الحر المستقل الذي لا يقبل التبعية.",
                "زينب": "اسم عربي يعني الشجرة الطيبة أو الجميلة."
            };

            const resultDiv = document.getElementById('result');
            if (meanings[name]) {
                resultDiv.textContent = `معنى اسم ${name}: ${meanings[name]}`;
            } else {
                resultDiv.textContent = "اسمك لا يوجد في القائمة، استمتع بيوم اللغة العربية!";
            }

            // تحديث عدد الزوار
            visitorCount++;
            document.getElementById('visitorCount').textContent = visitorCount;
        }

        // زيادة عدد الزوار بشكل تلقائي
        document.addEventListener('DOMContentLoaded', function() {
            visitorCount = localStorage.getItem('visitorCount') || 0;
            document.getElementById('visitorCount').textContent = visitorCount;
        });

        // تحديث عدد الزوار
        window.addEventListener('beforeunload', function() {
            localStorage.setItem('visitorCount', visitorCount);
        });

        // فتح موقع الخط المسند
        function openCalligraphySite() {
            const name = document.getElementById('nameInput').value.trim();
            if (name) {
                const url = `https://aip.ae/#tname=${name}`;
                window.open(url, '_blank');
            } else {
                alert("من فضلك أدخل اسمك أولاً.");
            }
        }
    </script>

</body>
</html>
