# emr
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="Personal Medical Record - 個人病歷管理">
<title>My Medical Record</title>

<style>
:root {
--bg: #f4f7fb;
--card: #ffffff;
--text: #172033;
--muted: #667085;
--primary: #2563eb;
--primary-dark: #1d4ed8;
--danger: #dc2626;
--success: #16a34a;
--border: #d9e0ea;
--input: #ffffff;
--shadow: 0 8px 30px rgba(15, 23, 42, .08);
}

* {
box-sizing: border-box;
}

body {
margin: 0;
font-family:
-apple-system,
BlinkMacSystemFont,
"Segoe UI",
"Noto Sans TC",
"Noto Sans",
Arial,
sans-serif;
background: var(--bg);
color: var(--text);
line-height: 1.6;
}

body.dark {
--bg: #101827;
--card: #182235;
--text: #f3f6fb;
--muted: #a8b3c5;
--border: #334155;
--input: #111a2b;
--shadow: 0 8px 30px rgba(0,0,0,.25);
}

header {
background: linear-gradient(135deg, #2563eb, #0ea5e9);
color: white;
padding: 28px 20px;
position: sticky;
top: 0;
z-index: 20;
box-shadow: 0 4px 20px rgba(0,0,0,.12);
}

.header-inner {
max-width: 1100px;
margin: auto;
display: flex;
align-items: center;
justify-content: space-between;
gap: 20px;
}

.logo {
display: flex;
align-items: center;
gap: 12px;
}

.logo-icon {
font-size: 38px;
}

.logo h1 {
margin: 0;
font-size: 24px;
}

.logo p {
margin: 2px 0 0;
opacity: .9;
font-size: 13px;
}

.header-actions {
display: flex;
gap: 8px;
flex-wrap: wrap;
justify-content: flex-end;
}

button,
select,
input,
textarea {
font: inherit;
}

button {
border: 0;
cursor: pointer;
}

.header-btn {
padding: 9px 13px;
border-radius: 9px;
background: rgba(255,255,255,.18);
color: white;
border: 1px solid rgba(255,255,255,.3);
}

.header-btn:hover {
background: rgba(255,255,255,.28);
}

.container {
width: min(1100px, calc(100% - 30px));
margin: 28px auto 60px;
}

.notice {
background: #fff7ed;
border: 1px solid #fed7aa;
color: #9a3412;
padding: 14px 16px;
border-radius: 12px;
margin-bottom: 20px;
}

.dark .notice {
background: #3a2415;
border-color: #7c3f16;
color: #fed7aa;
}

.toolbar {
display: flex;
gap: 10px;
flex-wrap: wrap;
margin-bottom: 20px;
}

.toolbar input {
flex: 1;
min-width: 220px;
}

.btn {
padding: 10px 15px;
border-radius: 9px;
background: #e5e7eb;
color: #111827;
transition: .2s;
}

.dark .btn {
background: #273449;
color: white;
}

.btn:hover {
transform: translateY(-1px);
}

.btn-primary {
background: var(--primary);
color: white;
}

.btn-primary:hover {
background: var(--primary-dark);
}

.btn-danger {
background: #fee2e2;
color: var(--danger);
}

.dark .btn-danger {
background: #451a1a;
}

.btn-success {
background: var(--success);
color: white;
}

.card {
background: var(--card);
border: 1px solid var(--border);
border-radius: 16px;
padding: 22px;
margin-bottom: 18px;
box-shadow: var(--shadow);
}

.card-title {
display: flex;
align-items: center;
justify-content: space-between;
gap: 10px;
margin-bottom: 18px;
}

.card-title h2 {
margin: 0;
font-size: 19px;
}

.card-title .icon {
font-size: 24px;
}

.grid {
display: grid;
grid-template-columns: repeat(2, minmax(0,1fr));
gap: 15px;
}

.field {
display: flex;
flex-direction: column;
gap: 6px;
}

.field.full {
grid-column: 1 / -1;
}

label {
font-size: 14px;
font-weight: 600;
}

input,
select,
textarea {
width: 100%;
padding: 11px 12px;
border: 1px solid var(--border);
border-radius: 9px;
background: var(--input);
color: var(--text);
outline: none;
}

input:focus,
select:focus,
textarea:focus {
border-color: var(--primary);
box-shadow: 0 0 0 3px rgba(37,99,235,.12);
}

textarea {
min-height: 100px;
resize: vertical;
}

.repeat-list {
display: flex;
flex-direction: column;
gap: 12px;
}

.repeat-item {
border: 1px solid var(--border);
border-radius: 12px;
padding: 15px;
position: relative;
}

.repeat-item .remove {
position: absolute;
right: 10px;
top: 10px;
padding: 5px 8px;
border-radius: 7px;
background: #fee2e2;
color: var(--danger);
}

.dark .repeat-item .remove {
background: #451a1a;
}

.repeat-grid {
display: grid;
grid-template-columns: repeat(2, minmax(0,1fr));
gap: 12px;
padding-right: 45px;
}

.add-btn {
margin-top: 12px;
border: 1px dashed var(--primary);
color: var(--primary);
background: transparent;
padding: 9px 14px;
border-radius: 9px;
}

.custom-section {
border-left: 4px solid var(--primary);
}

.custom-field-row {
display: grid;
grid-template-columns: 1fr 2fr auto;
gap: 10px;
align-items: end;
margin-bottom: 12px;
}

.status {
position: fixed;
right: 20px;
bottom: 20px;
background: #111827;
color: white;
padding: 11px 16px;
border-radius: 10px;
opacity: 0;
transform: translateY(10px);
pointer-events: none;
transition: .3s;
z-index: 100;
}

.status.show {
opacity: 1;
transform: translateY(0);
}

.footer {
text-align: center;
color: var(--muted);
font-size: 13px;
margin-top: 30px;
}

.hidden {
display: none !important;
}

@media (max-width: 700px) {
.header-inner {
align-items: flex-start;
flex-direction: column;
}

.header-actions {
justify-content: flex-start;
width: 100%;
}

.grid,
.repeat-grid {
grid-template-columns: 1fr;
}

.custom-field-row {
grid-template-columns: 1fr;
}

.container {
width: min(100% - 20px, 1100px);
margin-top: 15px;
}

.card {
padding: 16px;
}
}

@media print {
header {
position: static;
background: white;
color: black;
box-shadow: none;
}

.header-actions,
.toolbar,
.notice,
.add-btn,
.remove,
.footer {
display: none !important;
}

body,
.card {
background: white !important;
color: black !important;
box-shadow: none;
}

.card {
break-inside: avoid;
border: 1px solid #ccc;
}
}
</style>
</head>

<body>

<header>
<div class="header-inner">
<div class="logo">
<div class="logo-icon">🩺</div>
<div>
<h1 id="appTitle">我的個人病歷</h1>
<p id="appSubtitle">Personal Medical Record</p>
</div>
</div>

<div class="header-actions">
<select id="language" class="header-btn" onchange="changeLanguage()">
<option value="zh-TW">繁體中文</option>
<option value="en">English</option>
<option value="ja">日本語</option>
<option value="ko">한국어</option>
</select>

<button class="header-btn" onclick="toggleDarkMode()" id="darkBtn">
🌙 深色模式
</button>
</div>
</div>
</header>

<main class="container">

<div class="notice">
⚠️ <strong id="privacyTitle">隱私提醒：</strong>
<span id="privacyText">
本網站目前將資料儲存在此瀏覽器的 localStorage。
請勿在公用電腦輸入敏感醫療資料。此網站不能取代醫療專業人員的診斷。
</span>
</div>

<div class="toolbar">
<input
id="searchBox"
type="search"
placeholder="搜尋病歷內容..."
oninput="searchRecords()"
>

<button class="btn btn-primary" onclick="saveData()">
💾 <span data-i18n="save">儲存</span>
</button>

<button class="btn" onclick="exportData()">
📤 <span data-i18n="export">匯出</span>
</button>

<button class="btn" onclick="document.getElementById('importFile').click()">
📥 <span data-i18n="import">匯入</span>
</button>

<input
type="file"
id="importFile"
accept=".json"
class="hidden"
onchange="importData(event)"
>

<button class="btn" onclick="window.print()">
🖨️ <span data-i18n="print">列印</span>
</button>
</div>


<!-- 基本資料 -->
<section class="card searchable">
<div class="card-title">
<h2>👤 <span data-i18n="personal">個人基本資料</span></h2>
</div>

<div class="grid">
<div class="field">
<label data-i18n="name">姓名</label>
<input id="name" type="text">
</div>

<div class="field">
<label data-i18n="nickname">稱呼／暱稱</label>
<input id="nickname" type="text">
</div>

<div class="field">
<label data-i18n="birthday">出生日期</label>
<input id="birthday" type="date">
</div>

<div class="field">
<label data-i18n="gender">性別</label>
<select id="gender">
<option value=""></option>
<option>男</option>
<option>女</option>
<option>其他</option>
<option>不提供</option>
</select>
</div>

<div class="field">
<label data-i18n="phone">電話</label>
<input id="phone" type="tel">
</div>

<div class="field">
<label data-i18n="email">電子郵件</label>
<input id="email" type="email">
</div>

<div class="field">
<label data-i18n="country">國家／地區</label>
<input id="country" type="text">
</div>

<div class="field">
<label data-i18n="blood">血型</label>
<select id="bloodType">
<option value=""></option>
<option>A+</option>
<option>A-</option>
<option>B+</option>
<option>B-</option>
<option>AB+</option>
<option>AB-</option>
<option>O+</option>
<option>O-</option>
<option>不詳</option>
</select>
</div>

<div class="field full">
<label data-i18n="address">地址</label>
<input id="address" type="text">
</div>
</div>
</section>


<!-- 緊急聯絡人 -->
<section class="card searchable">
<div class="card-title">
<h2>📞 <span data-i18n="emergency">緊急聯絡人</span></h2>
</div>

<div class="grid">
<div class="field">
<label>姓名</label>
<input id="emergencyName">
</div>

<div class="field">
<label>關係</label>
<input id="emergencyRelation">
</div>

<div class="field">
<label>電話</label>
<input id="emergencyPhone">
</div>

<div class="field">
<label>備註</label>
<input id="emergencyNote">
</div>
</div>
</section>


<!-- 過敏 -->
<section class="card searchable">
<div class="card-title">
<h2>⚠️ <span data-i18n="allergies">過敏紀錄</span></h2>
</div>

<div id="allergyList" class="repeat-list"></div>

<button class="add-btn" onclick="addAllergy()">
＋ <span data-i18n="addAllergy">新增過敏</span>
</button>
</section>


<!-- 用藥 -->
<section class="card searchable">
<div class="card-title">
<h2>💊 <span data-i18n="medications">近期／目前用藥</span></h2>
</div>

<div id="medicationList" class="repeat-list"></div>

<button class="add-btn" onclick="addMedication()">
＋ <span data-i18n="addMedication">新增藥物</span>
</button>
</section>


<!-- 疾病 -->
<section class="card searchable">
<div class="card-title">
<h2>🦠 <span data-i18n="diseases">近期疾病／就醫紀錄</span></h2>
</div>

<div id="diseaseList" class="repeat-list"></div>

<button class="add-btn" onclick="addDisease()">
＋ <span data-i18n="addDisease">新增紀錄</span>
</button>
</section>


<!-- 慢性病 -->
<section class="card searchable">
<div class="card-title">
<h2>🏥 <span data-i18n="chronic">慢性病</span></h2>
</div>

<div id="chronicList" class="repeat-list"></div>

<button class="add-btn" onclick="addChronic()">
＋ <span data-i18n="addChronic">新增慢性病</span>
</button>
</section>


<!-- 手術 -->
<section class="card searchable">
<div class="card-title">
<h2>🔪 <span data-i18n="surgery">手術／住院史</span></h2>
</div>

<div id="surgeryList" class="repeat-list"></div>

<button class="add-btn" onclick="addSurgery()">
＋ <span data-i18n="addSurgery">新增紀錄</span>
</button>
</section>


<!-- 疫苗 -->
<section class="card searchable">
<div class="card-title">
<h2>💉 <span data-i18n="vaccines">疫苗紀錄</span></h2>
</div>

<div id="vaccineList" class="repeat-list"></div>

<button class="add-btn" onclick="addVaccine()">
＋ <span data-i18n="addVaccine">新增疫苗</span>
</button>
</section>


<!-- 醫療備註 -->
<section class="card searchable">
<div class="card-title">
<h2>📝 <span data-i18n="notes">其他醫療資訊</span></h2>
</div>

<div class="grid">
<div class="field full">
<label>醫師／醫院備註</label>
<textarea id="medicalNotes"></textarea>
</div>

<div class="field full">
<label>其他重要資訊</label>
<textarea id="importantNotes"></textarea>
</div>
</div>
</section>


<!-- 自訂欄位 -->
<section class="card custom-section searchable">
<div class="card-title">
<h2>➕ <span data-i18n="custom">自訂資料</span></h2>
</div>

<p style="color:var(--muted);margin-top:0;">
可以自由加入任何未包含在上面的醫療或個人資訊。
</p>

<div id="customFields"></div>

<button class="add-btn" onclick="addCustomField()">
＋ 新增自訂欄位
</button>
</section>


<div class="footer">
<span id="lastSaved">尚未儲存</span>
<br>
My Medical Record · Single HTML Edition
</div>

</main>

<div id="status" class="status"></div>


<script>
/* ============================================================
My Medical Record
Single-file HTML application
============================================================ */

const STORAGE_KEY = "my_medical_record_v1";

let currentLanguage = "zh-TW";

const translations = {

"zh-TW": {
title: "我的個人病歷",
subtitle: "Personal Medical Record",
dark: "深色模式",
save: "儲存",
export: "匯出",
import: "匯入",
print: "列印",
personal: "個人基本資料",
name: "姓名",
nickname: "稱呼／暱稱",
birthday: "出生日期",
gender: "性別",
phone: "電話",
email: "電子郵件",
country: "國家／地區",
blood: "血型",
address: "地址",
emergency: "緊急聯絡人",
allergies: "過敏紀錄",
medications: "近期／目前用藥",
diseases: "近期疾病／就醫紀錄",
chronic: "慢性病",
surgery: "手術／住院史",
vaccines: "疫苗紀錄",
notes: "其他醫療資訊",
custom: "自訂資料",
addAllergy: "新增過敏",
addMedication: "新增藥物",
addDisease: "新增紀錄",
addChronic: "新增慢性病",
addSurgery: "新增紀錄",
addVaccine: "新增疫苗",
privacyTitle: "隱私提醒：",
privacyText: "本網站目前將資料儲存在此瀏覽器的 localStorage。請勿在公用電腦輸入敏感醫療資料。此網站不能取代醫療專業人員的診斷。"
},

"en": {
title: "My Medical Record",
subtitle: "Personal Medical Record",
dark: "Dark Mode",
save: "Save",
export: "Export",
import: "Import",
print: "Print",
personal: "Personal Information",
name: "Name",
nickname: "Nickname",
birthday: "Date of Birth",
gender: "Gender",
phone: "Phone",
email: "Email",
country: "Country / Region",
blood: "Blood Type",
address: "Address",
emergency: "Emergency Contact",
allergies: "Allergies",
medications: "Current / Recent Medications",
diseases: "Recent Illness / Medical Visits",
chronic: "Chronic Conditions",
surgery: "Surgery / Hospitalization History",
vaccines: "Vaccination Records",
notes: "Other Medical Information",
custom: "Custom Information",
addAllergy: "Add Allergy",
addMedication: "Add Medication",
addDisease: "Add Record",
addChronic: "Add Condition",
addSurgery: "Add Record",
addVaccine: "Add Vaccine",
privacyTitle: "Privacy Notice:",
privacyText: "Your information is currently stored in this browser's localStorage. Avoid entering sensitive medical information on public computers. This website does not replace professional medical advice."
},

"ja": {
title: "個人医療記録",
subtitle: "Personal Medical Record",
dark: "ダークモード",
save: "保存",
export: "エクスポート",
import: "インポート",
print: "印刷",
personal: "基本情報",
name: "氏名",
nickname: "ニックネーム",
birthday: "生年月日",
gender: "性別",
phone: "電話番号",
email: "メール",
country: "国／地域",
blood: "血液型",
address: "住所",
emergency: "緊急連絡先",
allergies: "アレルギー",
medications: "現在／最近の薬",
diseases: "最近の病気／受診歴",
chronic: "慢性疾患",
surgery: "手術／入院歴",
vaccines: "ワクチン記録",
notes: "その他の医療情報",
custom: "カスタム情報",
addAllergy: "アレルギーを追加",
addMedication: "薬を追加",
addDisease: "記録を追加",
addChronic: "疾患を追加",
addSurgery: "記録を追加",
addVaccine: "ワクチンを追加",
privacyTitle: "プライバシー注意：",
privacyText: "情報は現在このブラウザのlocalStorageに保存されます。公共のコンピューターでは機密性の高い医療情報を入力しないでください。このサイトは医療専門家の診断に代わるものではありません。"
},

"ko": {
title: "개인 의료 기록",
subtitle: "Personal Medical Record",
dark: "다크 모드",
save: "저장",
export: "내보내기",
import: "가져오기",
print: "인쇄",
personal: "개인 기본 정보",
name: "이름",
nickname: "별명",
birthday: "생년월일",
gender: "성별",
phone: "전화번호",
email: "이메일",
country: "국가 / 지역",
blood: "혈액형",
address: "주소",
emergency: "응급 연락처",
allergies: "알레르기",
medications: "현재 / 최근 복용약",
diseases: "최근 질병 / 진료 기록",
chronic: "만성 질환",
surgery: "수술 / 입원 기록",
vaccines: "예방접종 기록",
notes: "기타 의료 정보",
custom: "사용자 정의 정보",
addAllergy: "알레르기 추가",
addMedication: "약 추가",
addDisease: "기록 추가",
addChronic: "질환 추가",
addSurgery: "기록 추가",
addVaccine: "백신 추가",
privacyTitle: "개인정보 안내:",
privacyText: "정보는 현재 이 브라우저의 localStorage에 저장됩니다. 공용 컴퓨터에서는 민감한 의료 정보를 입력하지 마세요. 이 웹사이트는 전문 의료진의 진단을 대체하지 않습니다."
}
};


/* ============================================================
Basic utilities
============================================================ */

function escapeHtml(value) {
return String(value || "")
.replace(/&/g, "&amp;")
.replace(/</g, "&lt;")
.replace(/>/g, "&gt;")
.replace(/"/g, "&quot;")
.replace(/'/g, "&#039;");
}

function showStatus(message) {
const el = document.getElementById("status");

el.textContent = message;
el.classList.add("show");

clearTimeout(window.statusTimer);

window.statusTimer = setTimeout(() => {
el.classList.remove("show");
}, 2200);
}

function id() {
return Date.now() + "_" + Math.random().toString(36).substring(2, 8);
}


/* ============================================================
Language
============================================================ */

function changeLanguage() {

currentLanguage = document.getElementById("language").value;

const t = translations[currentLanguage];

document.getElementById("appTitle").textContent = t.title;
document.getElementById("appSubtitle").textContent = t.subtitle;
document.getElementById("privacyTitle").textContent = t.privacyTitle;
document.getElementById("privacyText").textContent = t.privacyText;

document.querySelectorAll("[data-i18n]").forEach(el => {

const key = el.getAttribute("data-i18n");

if (t[key]) {
el.textContent = t[key];
}

});

document.getElementById("darkBtn").textContent =
"🌙 " + t.dark;

document.documentElement.lang =
currentLanguage === "zh-TW" ? "zh-Hant" :
currentLanguage;

saveData(false);
}


/* ============================================================
Dark mode
============================================================ */

function toggleDarkMode() {

document.body.classList.toggle("dark");

localStorage.setItem(
"medical_dark_mode",
document.body.classList.contains("dark") ? "1" : "0"
);
}


/* ============================================================
Dynamic records
============================================================ */

function addAllergy(data = {}) {

const list = document.getElementById("allergyList");

const div = document.createElement("div");

div.className = "repeat-item searchable";

div.dataset.id = data.id || id();

div.innerHTML = `
<button class="remove" onclick="this.parentElement.remove()">✕</button>

<div class="repeat-grid">

<div class="field">
<label>過敏原／Allergen</label>
<input class="a-name" value="${escapeHtml(data.name)}">
</div>

<div class="field">
<label>反應／Reaction</label>
<input class="a-reaction" value="${escapeHtml(data.reaction)}">
</div>

<div class="field">
<label>嚴重程度／Severity</label>
<select class="a-severity">
<option value="">未指定</option>
<option ${data.severity === "輕微" ? "selected" : ""}>輕微</option>
<option ${data.severity === "中等" ? "selected" : ""}>中等</option>
<option ${data.severity === "嚴重" ? "selected" : ""}>嚴重</option>
</select>
</div>

<div class="field">
<label>備註／Notes</label>
<input class="a-note" value="${escapeHtml(data.note)}">
</div>

</div>
`;

list.appendChild(div);
}


function addMedication(data = {}) {

const list = document.getElementById("medicationList");

const div = document.createElement("div");

div.className = "repeat-item searchable";

div.dataset.id = data.id || id();

div.innerHTML = `
<button class="remove" onclick="this.parentElement.remove()">✕</button>

<div class="repeat-grid">

<div class="field">
<label>藥物名稱／Medication</label>
<input class="m-name" value="${escapeHtml(data.name)}">
</div>

<div class="field">
<label>劑量／Dosage</label>
<input class="m-dose" value="${escapeHtml(data.dose)}">
</div>

<div class="field">
<label>頻率／Frequency</label>
<input class="m-frequency" value="${escapeHtml(data.frequency)}">
</div>

<div class="field">
<label>開始日期／Start Date</label>
<input class="m-start" type="date" value="${escapeHtml(data.start)}">
</div>

<div class="field">
<label>處方醫師／Doctor</label>
<input class="m-doctor" value="${escapeHtml(data.doctor)}">
</div>

<div class="field">
<label>備註／Notes</label>
<input class="m-note" value="${escapeHtml(data.note)}">
</div>

</div>
`;

list.appendChild(div);
}


function addDisease(data = {}) {

const list = document.getElementById("diseaseList");

const div = document.createElement("div");

div.className = "repeat-item searchable";

div.dataset.id = data.id || id();

div.innerHTML = `
<button class="remove" onclick="this.parentElement.remove()">✕</button>

<div class="repeat-grid">

<div class="field">
<label>疾病／Diagnosis</label>
<input class="d-name" value="${escapeHtml(data.name)}">
</div>

<div class="field">
<label>日期／Date</label>
<input class="d-date" type="date" value="${escapeHtml(data.date)}">
</div>

<div class="field">
<label>醫院／Clinic</label>
<input class="d-clinic" value="${escapeHtml(data.clinic)}">
</div>

<div class="field">
<label>醫師／Doctor</label>
<input class="d-doctor" value="${escapeHtml(data.doctor)}">
</div>

<div class="field full">
<label>症狀／Details</label>
<textarea class="d-details">${escapeHtml(data.details)}</textarea>
</div>

</div>
`;

list.appendChild(div);
}


function addChronic(data = {}) {

const list = document.getElementById("chronicList");

const div = document.createElement("div");

div.className = "repeat-item searchable";

div.dataset.id = data.id || id();

div.innerHTML = `
<button class="remove" onclick="this.parentElement.remove()">✕</button>

<div class="repeat-grid">

<div class="field">
<label>慢性病／Condition</label>
<input class="c-name" value="${escapeHtml(data.name)}">
</div>

<div class="field">
<label>確診日期／Diagnosis Date</label>
<input class="c-date" type="date" value="${escapeHtml(data.date)}">
</div>

<div class="field">
<label>目前狀態／Status</label>
<input class="c-status" value="${escapeHtml(data.status)}">
</div>

<div class="field">
<label>主治醫師／Doctor</label>
<input class="c-doctor" value="${escapeHtml(data.doctor)}">
</div>

<div class="field full">
<label>說明／Details</label>
<textarea class="c-details">${escapeHtml(data.details)}</textarea>
</div>

</div>
`;

list.appendChild(div);
}


function addSurgery(data = {}) {

const list = document.getElementById("surgeryList");

const div = document.createElement("div");

div.className = "repeat-item searchable";

div.dataset.id = data.id || id();

div.innerHTML = `
<button class="remove" onclick="this.parentElement.remove()">✕</button>

<div class="repeat-grid">

<div class="field">
<label>手術／住院項目</label>
<input class="s-name" value="${escapeHtml(data.name)}">
</div>

<div class="field">
<label>日期</label>
<input class="s-date" type="date" value="${escapeHtml(data.date)}">
</div>

<div class="field">
<label>醫院</label>
<input class="s-hospital" value="${escapeHtml(data.hospital)}">
</div>

<div class="field">
<label>醫師</label>
<input class="s-doctor" value="${escapeHtml(data.doctor)}">
</div>

<div class="field full">
<label>備註</label>
<textarea class="s-note">${escapeHtml(data.note)}</textarea>
</div>

</div>
`;

list.appendChild(div);
}


function addVaccine(data = {}) {

const list = document.getElementById("vaccineList");

const div = document.createElement("div");

div.className = "repeat-item searchable";

div.dataset.id = data.id || id();

div.innerHTML = `
<button class="remove" onclick="this.parentElement.remove()">✕</button>

<div class="repeat-grid">

<div class="field">
<label>疫苗名稱／Vaccine</label>
<input class="v-name" value="${escapeHtml(data.name)}">
</div>

<div class="field">
<label>接種日期／Date</label>
<input class="v-date" type="date" value="${escapeHtml(data.date)}">
</div>

<div class="field">
<label>劑次／Dose</label>
<input class="v-dose" value="${escapeHtml(data.dose)}">
</div>

<div class="field">
<label>接種地點／Location</label>
<input class="v-location" value="${escapeHtml(data.location)}">
</div>

<div class="field full">
<label>備註／Notes</label>
<textarea class="v-note">${escapeHtml(data.note)}</textarea>
</div>

</div>
`;

list.appendChild(div);
}


function addCustomField(data = {}) {

const container = document.getElementById("customFields");

const div = document.createElement("div");

div.className = "custom-field-row searchable";

div.dataset.id = data.id || id();

div.innerHTML = `
<div class="field">
<label>欄位名稱</label>
<input class="custom-name" value="${escapeHtml(data.name)}">
</div>

<div class="field">
<label>內容</label>
<input class="custom-value" value="${escapeHtml(data.value)}">
</div>

<button
class="btn btn-danger"
onclick="this.parentElement.remove()">
🗑️
</button>
`;

container.appendChild(div);
}


/* ============================================================
Collect data
============================================================ */

function collectData() {

const data = {

version: 1,

savedAt: new Date().toISOString(),

language: currentLanguage,

personal: {
name: document.getElementById("name").value,
nickname: document.getElementById("nickname").value,
birthday: document.getElementById("birthday").value,
gender: document.getElementById("gender").value,
phone: document.getElementById("phone").value,
email: document.getElementById("email").value,
country: document.getElementById("country").value,
bloodType: document.getElementById("bloodType").value,
address: document.getElementById("address").value
},

emergency: {
name: document.getElementById("emergencyName").value,
relation: document.getElementById("emergencyRelation").value,
phone: document.getElementById("emergencyPhone").value,
note: document.getElementById("emergencyNote").value
},

allergies: [],

medications: [],

diseases: [],

chronic: [],

surgeries: [],

vaccines: [],

medicalNotes: document.getElementById("medicalNotes").value,

importantNotes: document.getElementById("importantNotes").value,

customFields: []
};


document.querySelectorAll("#allergyList .repeat-item").forEach(el => {

data.allergies.push({
id: el.dataset.id,
name: el.querySelector(".a-name").value,
reaction: el.querySelector(".a-reaction").value,
severity: el.querySelector(".a-severity").value,
note: el.querySelector(".a-note").value
});

});


document.querySelectorAll("#medicationList .repeat-item").forEach(el => {

data.medications.push({
id: el.dataset.id,
name: el.querySelector(".m-name").value,
dose: el.querySelector(".m-dose").value,
frequency: el.querySelector(".m-frequency").value,
start: el.querySelector(".m-start").value,
doctor: el.querySelector(".m-doctor").value,
note: el.querySelector(".m-note").value
});

});


document.querySelectorAll("#diseaseList .repeat-item").forEach(el => {

data.diseases.push({
id: el.dataset.id,
name: el.querySelector(".d-name").value,
date: el.querySelector(".d-date").value,
clinic: el.querySelector(".d-clinic").value,
doctor: el.querySelector(".d-doctor").value,
details: el.querySelector(".d-details").value
});

});


document.querySelectorAll("#chronicList .repeat-item").forEach(el => {

data.chronic.push({
id: el.dataset.id,
name: el.querySelector(".c-name").value,
date: el.querySelector(".c-date").value,
status: el.querySelector(".c-status").value,
doctor: el.querySelector(".c-doctor").value,
details: el.querySelector(".c-details").value
});

});


document.querySelectorAll("#surgeryList .repeat-item").forEach(el => {

data.surgeries.push({
id: el.dataset.id,
name: el.querySelector(".s-name").value,
date: el.querySelector(".s-date").value,
hospital: el.querySelector(".s-hospital").value,
doctor: el.querySelector(".s-doctor").value,
note: el.querySelector(".s-note").value
});

});


document.querySelectorAll("#vaccineList .repeat-item").forEach(el => {

data.vaccines.push({
id: el.dataset.id,
name: el.querySelector(".v-name").value,
date: el.querySelector(".v-date").value,
dose: el.querySelector(".v-dose").value,
location: el.querySelector(".v-location").value,
note: el.querySelector(".v-note").value
});

});


document.querySelectorAll("#customFields .custom-field-row").forEach(el => {

data.customFields.push({
id: el.dataset.id,
name: el.querySelector(".custom-name").value,
value: el.querySelector(".custom-value").value
});

});


return data;
}


/* ============================================================
Save
============================================================ */

function saveData(showMessage = true) {

const data = collectData();

localStorage.setItem(
STORAGE_KEY,
JSON.stringify(data)
);

const time = new Date().toLocaleString();

document.getElementById("lastSaved").textContent =
"最後儲存：" + time;

if (showMessage) {
showStatus("✓ 資料已儲存");
}
}


/* ============================================================
Load
============================================================ */

function loadData() {

const raw = localStorage.getItem(STORAGE_KEY);

if (!raw) {

addAllergy();
addMedication();
addDisease();
addChronic();
addSurgery();
addVaccine();

return;
}

try {

const data = JSON.parse(raw);

const p = data.personal || {};

document.getElementById("name").value = p.name || "";
document.getElementById("nickname").value = p.nickname || "";
document.getElementById("birthday").value = p.birthday || "";
document.getElementById("gender").value = p.gender || "";
document.getElementById("phone").value = p.phone || "";
document.getElementById("email").value = p.email || "";
document.getElementById("country").value = p.country || "";
document.getElementById("bloodType").value = p.bloodType || "";
document.getElementById("address").value = p.address || "";


const e = data.emergency || {};

document.getElementById("emergencyName").value = e.name || "";
document.getElementById("emergencyRelation").value = e.relation || "";
document.getElementById("emergencyPhone").value = e.phone || "";
document.getElementById("emergencyNote").value = e.note || "";


document.getElementById("medicalNotes").value =
data.medicalNotes || "";

document.getElementById("importantNotes").value =
data.importantNotes || "";


document.getElementById("allergyList").innerHTML = "";

(data.allergies || []).forEach(addAllergy);


document.getElementById("medicationList").innerHTML = "";

(data.medications || []).forEach(addMedication);


document.getElementById("diseaseList").innerHTML = "";

(data.diseases || []).forEach(addDisease);


document.getElementById("chronicList").innerHTML = "";

(data.chronic || []).forEach(addChronic);


document.getElementById("surgeryList").innerHTML = "";

(data.surgeries || []).forEach(addSurgery);


document.getElementById("vaccineList").innerHTML = "";

(data.vaccines || []).forEach(addVaccine);


document.getElementById("customFields").innerHTML = "";

(data.customFields || []).forEach(addCustomField);


if (!data.allergies?.length) addAllergy();
if (!data.medications?.length) addMedication();
if (!data.diseases?.length) addDisease();
if (!data.chronic?.length) addChronic();
if (!data.surgeries?.length) addSurgery();
if (!data.vaccines?.length) addVaccine();


if (data.language) {

currentLanguage = data.language;

document.getElementById("language").value =
data.language;

changeLanguage();
}

} catch (error) {

console.error(error);

showStatus("⚠️ 無法讀取資料");

}
}


/* ============================================================
Export
============================================================ */

function exportData() {

const data = collectData();

const blob = new Blob(
[JSON.stringify(data, null, 2)],
{ type: "application/json" }
);

const url = URL.createObjectURL(blob);

const a = document.createElement("a");

const date = new Date()
.toISOString()
.slice(0, 10);

a.href = url;

a.download =
"medical-record-" +
date +
".json";

document.body.appendChild(a);

a.click();

a.remove();

URL.revokeObjectURL(url);

showStatus("✓ 已匯出病歷資料");
}


/* ============================================================
Import
============================================================ */

function importData(event) {

const file = event.target.files[0];

if (!file) return;

const reader = new FileReader();

reader.onload = function(e) {

try {

const data = JSON.parse(e.target.result);

localStorage.setItem(
STORAGE_KEY,
JSON.stringify(data)
);

loadData();

showStatus("✓ 匯入成功");

} catch (error) {

showStatus("⚠️ JSON 檔案格式錯誤");

}

event.target.value = "";

};

reader.readAsText(file);
}


/* ============================================================
Search
============================================================ */

function searchRecords() {

const query =
document.getElementById("searchBox")
.value
.trim()
.toLowerCase();

document.querySelectorAll(".searchable").forEach(el => {

if (!query) {

el.classList.remove("hidden");

return;
}

const text =
el.innerText.toLowerCase();

if (text.includes(query)) {

el.classList.remove("hidden");

} else {

el.classList.add("hidden");

}

});
}


/* ============================================================
Auto save
============================================================ */

let autoSaveTimer;

document.addEventListener("input", () => {

clearTimeout(autoSaveTimer);

autoSaveTimer = setTimeout(() => {

saveData(false);

}, 800);

});


/* ============================================================
Initialization
============================================================ */

window.addEventListener("DOMContentLoaded", () => {

if (localStorage.getItem("medical_dark_mode") === "1") {

document.body.classList.add("dark");

}

loadData();

});
</script>

</body>
</html>
