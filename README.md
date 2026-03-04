<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<title>كرت معايدة المدرسة</title>

<style>
body {
    text-align: center;
    font-family: Arial, sans-serif;
    background: #f4f4f4;
    direction: rtl;
}

h1 {
    margin-top: 30px;
    color: #0a3d62; /* لون اسم المدرسة */
}

h2 {
    margin-bottom: 20px;
}

input {
    padding: 10px;
    font-size: 18px;
    width: 300px;
}

button {
    padding: 10px 20px;
    font-size: 18px;
    cursor: pointer;
    margin: 5px;
}

.card {
    width: 1200px;   /* عدّل حسب عرض الصورة */
    height: 800px;   /* عدّل حسب ارتفاع الصورة */
    background: url('card.png') no-repeat center;
    background-size: cover;
    margin: 30px auto;
    position: relative;
    display: none;
    border-radius: 20px;
}

/* مكان الاسم داخل الكرت */
.name {
    position: absolute;
    bottom: 150px;      /* المسافة من أسفل الصورة */
    width: 100%;
    font-size: 70px;    /* حجم الخط */
    font-weight: bold;
    color: #004aad;     /* اللون الأزرق */
    text-align: center;
}
</style>

</head>
<body>

<h1>مدارس الأكاديمية العصرية</h1>
<h2>اكتب اسمك واستلم كرت المعايدة 🎉</h2>

<input type="text" id="studentName" placeholder="اكتب اسمك هنا">
<br>
<button onclick="generateCard()">إنشاء الكرت</button>
<button onclick="downloadCard()">تحميل الكرت كصورة 📥</button>

<div class="card" id="card">
    <div class="name" id="nameDisplay"></div>
</div>

<!-- مكتبة html2canvas لتحويل الكرت لصورة -->
<script src="https://cdn.jsdelivr.net/npm/html2canvas@1.4.1/dist/html2canvas.min.js"></script>

<script>
function generateCard() {
    var name = document.getElementById("studentName").value;

    if(name.trim() === "") {
        alert("اكتب اسمك أولاً");
        return;
    }

    document.getElementById("nameDisplay").innerText = name;
    document.getElementById("card").style.display = "block";
}

function downloadCard() {
    var card = document.getElementById("card");

    if(card.style.display === "none") {
        alert("أولاً أنشئ الكرت بكتابة الاسم!");
        return;
    }

    html2canvas(card).then(function(canvas) {
        var link = document.createElement('a');
        link.download = 'Eid_Card.png';  // اسم الصورة عند التحميل
        link.href = canvas.toDataURL();
        link.click();
    });
}
</script>

</body>
</html>
