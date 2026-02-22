# lomi-house-feedback
Should be like a game

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>🍜 Lomi House Feedback System</title>

<style>
@import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap');

body {
    font-family: 'Press Start 2P', cursive;
    background: #D2691E;
    background-image: repeating-linear-gradient(
        45deg,
        rgba(255,255,255,0.05) 0px,
        rgba(255,255,255,0.05) 2px,
        transparent 2px,
        transparent 6px
    );
    margin: 0;
    padding: 20px;
    text-align: center;
    image-rendering: pixelated;
}

h1 {
    font-size: 22px;
    color: #5D2E0F;
}

.pixel-box {
    background: #F5DEB3;
    border: 5px solid #5D2E0F;
    padding: 20px;
    margin: 20px auto;
    max-width: 800px;
}

.hidden {
    display: none;
}

button {
    font-family: 'Press Start 2P', cursive;
    background: #8B4513;
    color: white;
    border: 3px solid #5D2E0F;
    padding: 10px;
    cursor: pointer;
    margin: 10px;
}

button:hover {
    background: #A0522D;
}

.back-btn {
    float: left;
}

.section-title {
    margin-top: 20px;
    font-size: 14px;
    color: #5D2E0F;
}

.subtitle {
    font-size: 10px;
}

.question-item {
    margin: 20px 0;
}

.question-label {
    display: block;
    margin-bottom: 10px;
    font-size: 10px;
}

.star-rating {
    display: flex;
    justify-content: center;
    gap: 10px;
}

.star {
    font-size: 28px;
    cursor: pointer;
    color: #ccc;
}

.star.selected {
    color: gold;
}

/* Thank You Screen */
.thank-you-icon {
    font-size: 80px;
    margin: 20px 0;
    animation: bounce 1s infinite;
}

@keyframes bounce {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-15px); }
}

.thank-you-message {
    font-size: 12px;
    color: #5D2E0F;
    line-height: 2;
    margin: 20px 0;
}

/* Mobile */
@media (max-width: 768px) {
    h1 { font-size: 16px; }
    .star { font-size: 22px; }
}
</style>
</head>

<body>

<!-- HOME SCREEN -->
<div id="homeScreen">
    <div class="pixel-box">
        <h1>🍜 SELECT LOMI HOUSE</h1>
        <button onclick="selectRestaurant('Nog\'s Lomi House')">Nog's</button>
        <button onclick="selectRestaurant('Queen Lomi House')">Queen Lomi</button>
    </div>
</div>

<!-- FEEDBACK FORM -->
<div id="formScreen" class="hidden">
    <div class="pixel-box">
        <button class="back-btn" onclick="backToHome()">← BACK</button>
        <h1 id="restaurantTitle">🍜 FEEDBACK FORM</h1>

        <form id="feedbackForm">

            <div class="section-title">PART 1: SERVICE QUALITY</div>
            <p class="subtitle">Rate 1-5 stars (1=Very Poor, 5=Excellent)</p>

            <div class="section-title">1. TANGIBLES</div>

            <div class="question-item">
                <label class="question-label">Cleanliness of dining area</label>
                <div class="star-rating" data-question="area"></div>
            </div>

            <div class="question-item">
                <label class="question-label">Cleanliness of utensils</label>
                <div class="star-rating" data-question="utensils"></div>
            </div>

            <div class="question-item">
                <label class="question-label">Appearance of staff</label>
                <div class="star-rating" data-question="staff"></div>
            </div>

            <div class="section-title">2. RELIABILITY</div>

            <div class="question-item">
                <label class="question-label">Accuracy of orders</label>
                <div class="star-rating" data-question="accuracy"></div>
            </div>

            <div class="question-item">
                <label class="question-label">Consistency of food quality</label>
                <div class="star-rating" data-question="quality"></div>
            </div>

            <button type="button" onclick="submitFeedback()">SUBMIT</button>
        </form>
    </div>
</div>

<!-- THANK YOU SCREEN -->
<div id="thankYouScreen" class="hidden">
    <div class="pixel-box">
        <div class="thank-you-icon">🍜</div>
        <div class="thank-you-message">
            THANK YOU FOR YOUR FEEDBACK!<br>
            YOUR OPINION HELPS US IMPROVE!
        </div>
        <button onclick="backToHome()">BACK TO HOME</button>
    </div>
</div>

<script>
function selectRestaurant(name) {
    document.getElementById("homeScreen").classList.add("hidden");
    document.getElementById("formScreen").classList.remove("hidden");
    document.getElementById("restaurantTitle").innerText = "🍜 " + name + " FEEDBACK";
}

function backToHome() {
    document.getElementById("formScreen").classList.add("hidden");
    document.getElementById("thankYouScreen").classList.add("hidden");
    document.getElementById("homeScreen").classList.remove("hidden");
}

function submitFeedback() {
    document.getElementById("formScreen").classList.add("hidden");
    document.getElementById("thankYouScreen").classList.remove("hidden");
}

/* Create Stars */
document.querySelectorAll('.star-rating').forEach(container => {
    for (let i = 1; i <= 5; i++) {
        let star = document.createElement('span');
        star.innerHTML = "★";
        star.classList.add('star');
        star.addEventListener('click', function() {
            let stars = container.querySelectorAll('.star');
            stars.forEach((s, index) => {
                s.classList.toggle('selected', index < i);
            });
        });
        container.appendChild(star);
    }
});
</script>

</body>
</html>
