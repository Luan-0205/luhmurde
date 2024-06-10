const questions = [
    "Telefonou para a vítima?","Esteve no local da ocorrência?", "Mora perto da vítima?","Já trabalhou com a vítima?","Devia para a vítima?", "Conhecia a rotina da vítima?", "Tinha algum desentendimento com a vítima?","Estava na cidade no dia do ocorrido?",  "Foi visto com a vítima recentemente?","Tem algum motivo para prejudicar a vítima?"
];
let currentQuestionIndex = 0;
let yesCount = 0;

function showQuestion() {
document.getElementById('question').textContent = questions[currentQuestionIndex];
}
function answerQuestion(answer) {
    if (answer) yesCount++;
    
    currentQuestionIndex++;
    
    if (currentQuestionIndex < questions.length) {
        showQuestion();
    } else {
        showResult();
    }
}

function showResult() {
    const resultContainer = document.getElementById('result-container');
    const questionContainer = document.getElementById('question-container');
    const result = document.getElementById('result');
    
    questionContainer.classList.add('hidden');
    resultContainer.classList.remove('hidden');
    
    let resultText = '';
    
    if (yesCount === 5) {
        resultText = 'Suspeito, conversa mais comigo';
    } else if (yesCount >= 6 && yesCount <= 8) {
        resultText = 'Cúmplice, PRESO!';
    } else if (yesCount >= 9) {
        resultText = 'Culpado, PRESO!';
    } else {
        resultText = 'Inocente, VAZA DAQUI!';
    }
    
    result.textContent = `Você é: ${resultText}`;
}
//QUASE IMPOSSÍVEL O TRECHO ABAIXO
function resetQuiz() {
    currentQuestionIndex = 0;
    yesCount = 0;
    
    document.getElementById('question-container').classList.remove('hidden');
    document.getElementById('result-container').classList.add('hidden');
    
    showQuestion();
}

document.addEventListener('DOMContentLoaded', () => {
    showQuestion();
});