<template>
    <div id="game_home">
        <div id="hearts_container">
            <p class="lives">:חיים</p>
            <img src="../assets/gameSymbols/HeartsSymbol.svg" alt="heart" id="first_heart" class="hearts"/>
            <img src="../assets/gameSymbols/HeartsSymbol.svg" alt="heart" id="second_heart" class="hearts"/>
            <img src="../assets/gameSymbols/HeartsSymbol.svg" alt="heart" id="third_heart" class="hearts"/>
        </div>
        <div id="question_container">
           <h2 id="question" v-if="saveName === 0" :key="program[currentQuestion].question">{{ program[currentQuestion].question }}</h2>
           <h2 id="question" v-if="saveName === 1" :key="faculty[currentQuestion].question">{{ faculty[currentQuestion].question }}</h2>
           <h2 id="question" v-if="saveName === 2" :key="students[currentQuestion].question">{{ students[currentQuestion].question }}</h2>
           </div>
        <div id="choices_container">
          <div v-if="saveName === 0">
          <div id="choices" v-for="(answer, index) in program[currentQuestion].answers" :key="index"  v-bind:data-index="index">
            <p id="text_answer" @click="selectAnswer" v-if="saveName === 0">{{ answer }}</p>
          </div>
          </div>
          <div v-if="saveName === 1">
           <div id="choices" v-for="(answer, index) in faculty[currentQuestion].answers" :key="index"  v-bind:data-index="index" >
            <p id="text_answer" @click="selectAnswer">{{ answer }}</p>
           </div>
          </div>
          <div  v-if="saveName === 2">
          <div id="choices" v-for="(answer, index) in students[currentQuestion].answers" :key="index"  v-bind:data-index="index">
            <p id="text_answer" @click="selectAnswer" >{{ answer }}</p>
          </div>
          </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "game-home",
    props: ['subNumber'],
    data(){
        return {
            program: [
            {
            question: '',
            answers: [
                '',
                ' ',
            ],
            correct_answer: '',
            },
            {
            question: '',
            answers: [
                '',
                '',
                '',
                ''
            ],
            correct_answer: '',
            },
            {
            question: '',
            answers: [
                '',
                '',
                '',
                ''
            ],
            correct_answer: '',
            },
            {
            question: 'מה צריך לעשות טרם מבחן הערכת חניך, עיוני ומעשי?',
            answers: [
                'בעיוני יש לפרסם לחניכים את הנושאים עליהם הם עתידים להיבחן. במעשי יש לפרסם את דף ההערכה.',
                'בעיוני יש לפרסם את התשובות למבחן. במעשי יש לפרסם את דף ההערכה',
                'בעיוני יש לפרסם לחניכים את הנושאים עליהם הם עתידים להיבחן. במעשי יש לפרסם את מזג האוויר',
                
            ],
            correct_answer: 'בעיוני יש לפרסם לחניכים את הנושאים עליהם הם עתידים להיבחן. במעשי יש לפרסם את דף ההערכה.',
            },
                   {
            question: 'נכון או לא נכון: לכל מבחן עיוני ייבנה דף הערכה אשר יכלול את הקריטריונים להערכת הביצוע של הנבחן.',
            answers: [
                'נכון',
                'לא נכון, מדובר על מבחן מעשי ולא עיוני',
            ],
            correct_answer: 'לא נכון, מדובר על מבחן מעשי ולא עיוני',
            },
                   {
            question: 'למה נועד תיק מדריך?',
            answers: [
                'התיק נועד לאפשר למדריך לדעת את השמות של החניכים',
                'התיק נועד לאגד את כלל הנספחים הקשורים לשיעור: תמונות, תרשימים וציורים',
                'התיק נועד לאפשר הכנה מקצועית של המפקד או מדריך, להביא לאחידות מקצועית ולתרום לזיכרון הארגוני.',
                'התיק נועד לאפשר סדר וארגון למדריכים על מנת להקל על הסגל'
            ],
            correct_answer: 'התיק נועד לאפשר הכנה מקצועית של המפקד או מדריך, להביא לאחידות מקצועית ולתרום לזיכרון הארגוני.',
            }, 
            ],
            faculty: [
            {
            question: 'איך נקרא האחראי על תכנון וביצוע הכנות סגל למפקדים',
            answers: [
                'רמ"ד',
                'מפקד הכיתה',
                'קצין מגמה',
                'מדריך'
            ],
            correct_answer: 'קצין מגמה',
            },
            {
            question: '',
            answers: [
                '',
                ' ',
            ],
            correct_answer: '',
            },
            {
            question: '"הכנת סגל תבנה בחילוק לארבעה צירים", בחר בתשובה השייכת לארבעת הצירים.',
            answers: [
                'הציר הפיקודי',
                'הציר המעשי',
                'הציר העיוני',
                'הציר הרפואי'
            ],
            correct_answer: 'הציר הפיקודי',
            }, 
            {
            question: 'מה הוא פיתוח והערכת מפקדים?',
            answers: [
                'תהליך לאבחון רפואי של מפקדים',
                'תהליך שיטתי ומובן, המאורגן מראש הנותן מענה לצורך הפיקוד',
                'תהליך שיטתי ומובן, המאורגן בתוכנית קבועה מראש. התהליך מתחיל מיום קליטתו ועד סיום תפקידו.',
                'מאגד את כל ציוני המפקדים בקמפוס הדיגיטלי'
            ],
            correct_answer:  'תהליך שיטתי ומובן, המאורגן בתוכנית קבועה מראש. התהליך מתחיל מיום קליטתו ועד סיום תפקידו.',
            },
             {
            question: '',
            answers: [
                '',
                '',
                '',
                ''
            ],
            correct_answer: '',
            },
            {
            question: '',
            answers: [
                '',
                '',
                '',
                ''
            ],
            correct_answer: '',
            },
            ],
            students: [
            {
            question: 'דרכי הפעולה לקידום חניך:',
            answers: [
                'הפסקות ארוכות יותר כדי לתת לחניך להתרענן יותר בין שיעור לשיעור',
                'שעות תיגבור, זמנים ללמידה עצמית, מועדי מבחנים חוזרים, התנסויות והצמדת חונך מקצועי.',
                'לשלוח אותו לשיחת נזיפה אצל המ"פ ובמידת הצורך אצל המג"ד',
                'לבקש מהחניך הכי טוב בכיתה להסביר לו את החומר'
            ],
            correct_answer: 'שעות תיגבור, זמנים ללמידה עצמית, מועדי מבחנים חוזרים, התנסויות והצמדת חונך מקצועי.',
            },
            {
            question: '',
            answers: [
                '',
                '',
                '',
                ''
            ],
            correct_answer:  '',
            },
            {
            question: '"תהליך בחירת חניך מצטיין וחניך למופת נועד..."',
            answers: [
                'להגביר את הרצון להשקיע בהכשרה ולתגמל חניכים שהשקיעו.',
                'לתגמל את החייל שהכי טוב בעיניי המפקד',
                'להגביר את הרצון להשקיע לאחר פקודה',
                'לתגמל חניכים שהשקיעו במשימה'
            ],
            correct_answer: 'להגביר את הרצון להשקיע בהכשרה ולתגמל חניכים שהשקיעו.',
            },
            {
            question: 'מה מהבאים הוא מרכיב להצטיינות מופת?',
            answers: [
                'כושר קרבי',
                'מצטיין בר אור',
                'סוציומטרי עמיתים גבוה',
                'ציון סופי מעל 80'
            ],
            correct_answer: 'סוציומטרי עמיתים גבוה',
            },
            {
            question: 'מה הוא תיק אישי לחניך?',
            answers: [
                'תיק אישי לחניך משמש אמצעי לאיסוף המידע וריכוזו במכלול נושאים בעלי רלוונטיות לחניכים בקורס.',
                'תיק אישי לחניך משמש כלי לאיסוף מידע מישמעתי וציון סופי בהכשרה',
                'תיק אישי לחניך משמש אמצעי לאיסוף מידע משפחתי על החניך',
                'תיק אישי לחניך משמש אמצעי לאיסוף המידע הלימודי בלבד '
            ],
            correct_answer:  'תיק אישי לחניך משמש אמצעי לאיסוף המידע וריכוזו במכלול נושאים בעלי רלוונטיות לחניכים בקורס.',
            },
            {
            question: '',
            answers: [
                '',
                '',
                '',
                ''
            ],
            correct_answer: '',
            },
            ], 
            currentQuestion: 0,
            answered: 0,
            wrongAnswers: 0, 
            correctAnswers: 0,
            saveName: this.subNumber,
        }
    },
        methods: {
            selectAnswer(event){
                var MyAnswer = event.target.innerText;
                this.answered = this.answered + 1;

                if(this.answered === 6){
                    this.correctAnswers = this.correctAnswers + 1;
                    this.startOver();
                }
                
            switch(this.saveName) {
                case 0:
                    if(MyAnswer !== this.program[this.currentQuestion].correct_answer){
                         this.checkAnswer();
                    }else {
                        this.correctAnswers = this.correctAnswers + 1;
                        this.currentQuestion = this.currentQuestion + 1;
                    }
                break;
                case 1:
                    if(MyAnswer !== this.faculty[this.currentQuestion].correct_answer){
                         this.checkAnswer();
                    }else {
                        this.correctAnswers = this.correctAnswers + 1;
                        this.currentQuestion = this.currentQuestion + 1;
                    }
                break;
                case 2:
                    if(MyAnswer !== this.students[this.currentQuestion].correct_answer){
                         this.checkAnswer();
                    }else {
                        this.correctAnswers = this.correctAnswers + 1;
                        this.currentQuestion = this.currentQuestion + 1;
                    }
                break;
               default:
            }
            },

            checkAnswer(){
                this.currentQuestion = this.currentQuestion + 1;

                if(this.wrongAnswers === 0){
                        this.wrongAnswers = this.wrongAnswers + 1;
                        document.getElementById("third_heart").style.display = "none";
                }else if(this.wrongAnswers === 1){
                        this.wrongAnswers = this.wrongAnswers + 1;
                        document.getElementById("second_heart").style.display = "none";
                }else if(this.wrongAnswers === 2) {
                            document.getElementById("first_heart").style.display = "none";
                            this.wrongAnswers = this.wrongAnswers + 1;
                            this.startOver(); 
                }
            },

            startOver(){
                if(this.wrongAnswers === 3){
                    this.$emit("player-status", 1, this.correctAnswers);
                }else {
                    this.$emit("player-status", 0, this.correctAnswers);
                }
                 this.$emit("curr-page", 5);
            },
        }
}
</script>

<style scoped>
#game_home {
    background-image: url("../assets/photos/GameBackground.jpg");
    background-size: cover;
    background-repeat: no-repeat;
    height: 100%;
    width: 100%;
}

#question_container{
    position: absolute;
     height: 25vh;
     width: 72vw;
     left: 13vw;
     top: 10vh;
    background-image: url("../assets/gameSymbols/GameQuestionBox.svg");
    background-size: cover;
    background-attachment:inherit;
}

#question {
    position: absolute;
    width: 95%;
    height: 85%;
    top: 5%;
    left: 2.5%;
    color: white;
    font-family: MyFont;
    font-weight: 1000vw;
    font-size: 4.2vw;
    text-align: center;
    line-height: 41px;
    direction: rtl;
}

#deactivate {
  pointer-events: none;
}

#choices_container{
    position: absolute;
    height: 65vh;
    width: 80vw;
    left: 15vw;
    top: 37vh;
}

#choices{
    margin-bottom: 3%;
    background-image: url("../assets/gameSymbols/AnswerSymbol.svg");
    background-size: cover;
    background-repeat: no-repeat;
    width: 85%;
    height: 17%;
    direction: rtl;
}



#text_answer{
    position: absolute;
    color: white;
    width: 57%;
    height: 17%;
    left: 13%;
    font-family: MyFont;
    font-weight: 1000vw;
    font-size: 3.5vw;
    overflow-wrap: break-word;
    direction: rtl;
}


@font-face {
    font-family: MyFont;
    src: url("../assets/fonts/IBMPlexSansHebrew-Regular.ttf");
}

/* game hearts */

#hearts_container{
    position: absolute;
    height: 10vh;
    width: 55vw;
    right: 0vw;
    top: 0vh;
}

.lives{
    position: absolute;
    text-align: end;
    font-family: MyFont;
    font-size: 6vw;
    color: white;
    top: 7%;
}

#first_heart{
    position: absolute;
    height: 55%;
    width: 15%;
    left: 55%;
    top: 10%;
}

#second_heart{
    position: absolute;
    height: 55%;
    width: 15%;
    left: 35%;
    top: 10%;
}

#third_heart{
    position: absolute;
    height: 55%;
    width: 15%;
    left: 15%;
    top: 10%;
}
</style>