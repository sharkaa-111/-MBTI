[!DOCTYPE.html](https://github.com/user-attachments/files/27407196/DOCTYPE.html)
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<title>Chemistry MBTI</title>
<style>
    body { font-family: Arial; text-align: center; padding: 30px; }
    button { padding: 10px 20px; margin: 10px; font-size: 16px; }
    .hidden { display: none; }
</style>
</head>
<body>

<h1>🧪 화학 MBTI 테스트</h1>
<div id="quiz"></div>
<div id="result" class="hidden"></div>

<script>
const questions = [
    {q: "새로운 사람을 만났을 때 나는?", a: ["먼저 다가간다", "기다린다"], type: ["react","stable"]},
    {q: "혼자 있는 시간은?", a: ["지루하다", "편하다"], type: ["react","stable"]},
    {q: "스트레스 받을 때 나는?", a: ["바로 표출", "참는다"], type: ["explosive","stable"]},
    {q: "나의 인간관계 스타일은?", a: ["빠르게 친해짐", "천천히 친해짐"], type: ["react","bond"]},
    {q: "변화에 대한 태도?", a: ["좋아함", "싫어함"], type: ["react","stable"]},
    {q: "갈등 상황에 부딪혔을 때 나는?", a: ["부딪힘", "피함"], type: ["explosive","stable"]},
    {q: "내가 생각하는 나의 매력은?", a: ["활발함", "신뢰감"], type: ["react","bond"]},
    {q: "친구들이 보는 나는?", a: ["예측불가", "일정함"], type: ["radical","stable"]},

    // 🔽 추가 질문
    {q: "친구들 사이에서 나는?", a: ["분위기 메이커", "조용한 관찰자"], type: ["catalyst","noble"]},
    {q: "갈등 해결 방식?", a: ["직설적으로 말함", "부드럽게 풀어감"], type: ["acidic","basic"]},
    {q: "내 성격은?", a: ["단단하고 현실적", "유연하고 감성적"], type: ["metal","bond"]}
];

let current = 0;
let score = {
    react:0,
    stable:0,
    explosive:0,
    bond:0,
    radical:0,
    catalyst:0,
    acidic:0,
    basic:0,
    metal:0,
    noble:0
};

function showQuestion() {
    if (current >= questions.length) {
        showResult();
        return;
    }

    const q = questions[current];
    document.getElementById("quiz").innerHTML = `
        <h2>${q.q}</h2>
        <button onclick="answer(0)">${q.a[0]}</button>
        <button onclick="answer(1)">${q.a[1]}</button>
    `;
}

function answer(i) {
    score[questions[current].type[i]]++;
    current++;
    showQuestion();
}

function showResult() {
    document.getElementById("quiz").classList.add("hidden");

    let type = Object.keys(score).reduce((a,b)=>score[a]>score[b]?a:b);

    let resultText = "";
    let color = "";

    if (type==="react") { resultText = "🔥 Na형 인간\n반응 빠르고 활발!"; color="주황색"; }
    if (type==="stable") { resultText = "🧊 He형 인간\n안정 그 자체!"; color="하늘색"; }
    if (type==="explosive") { resultText = "💥 폭발형 인간\n감정 표현 확실!"; color="빨강"; }
    if (type==="bond") { resultText = "💧 H₂O형 인간\n친화력 최고!"; color="파랑"; }
    if (type==="radical") { resultText = "😈 라디칼형 인간\n위험하지만 매력!"; color="보라"; }

    if (type==="catalyst") { resultText = "⚡ 촉매형 인간\n분위기를 바꾸는 핵심 존재!"; color="보라"; }
    if (type==="acidic") { resultText = "🍋 산성형 인간\n솔직하고 직설적!"; color="레드"; }
    if (type==="basic") { resultText = "🧼 염기형 인간\n편안하고 안정적!"; color="파랑"; }
    if (type==="metal") { resultText = "🔩 금속형 인간\n단단하고 현실적!"; color="실버"; }
    if (type==="noble") { resultText = "🌌 비활성기체형 인간\n혼자서도 빛남!"; color="하늘"; }

    document.getElementById("result").classList.remove("hidden");
    document.getElementById("result").innerHTML = `
        <h2>결과</h2>
        <p style="white-space:pre-line;">${resultText}</p>
        <p>🎨 추천 키링 색상: <b>${color}</b></p>

    `;
}

showQuestion();
</script>

</body>
</html>
