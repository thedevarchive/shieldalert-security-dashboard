<template>
    <main class="mx-auto max-w-4xl px-6 py-10 text-white">
        <section class="mb-8">
            <p class="mb-2 font-semibold text-cyan-400">
                Information Security Management
            </p>
            <h1 class="mb-3 text-4xl font-bold">
                Midpoint Assessment
            </h1>

            <p class="mb-2 text-slate-300">
                Read each question carefully and select the best answer from the provided options.
            </p>
            <p class="mb-2 text-slate-300">
                The test will take about 30 minutes to complete.
            </p>
            <p class="mb-2 text-slate-300">
                You must score 70% to pass the test.
            </p>
        </section>

        <section class="rounded-2xl border border-slate-800 bg-slate-900 p-6" v-if="!quizFinished">
            <div class="mb-4 flex items-center justify-between" v-if="!hasAnswered">
                <p class="text-sm text-slate-400">
                    Question {{ currentQuestionIndex + 1 }} of {{ maxQuestions }}
                </p>

                <p class="text-sm text-slate-400">
                    Score: {{ score }}/{{ questions.length }}
                </p>
            </div>

            <div class="rounded-xl border border-slate-700 bg-slate-950 p-5" v-if="!hasAnswered">
                <p class="mb-2 text-sm text-slate-400">
                    {{ currentQuestion?.questionText }}
                </p>
            </div>

            <!-- User choices -->
            <div v-if="!hasAnswered" class="mt-6 flex flex-col gap-3">
                <button v-for="choice in currentChoices" @click="answerQuestion(choice)"
                    class="rounded-xl bg-slate-500 px-5 py-3 font-medium text-white transition hover:bg-slate-400">
                    {{ choice }}
                </button>
            </div>

            <div v-else class="mt-6 rounded-xl border p-5"
                :class="isCorrect ? 'border-emerald-500 bg-emerald-950/40' : 'border-red-500 bg-red-950/40'">
                <p v-if="!isCorrect" class="mb-2 text-lg text-slate-300">
                    You answered: <strong>{{ selectedAnswer }}</strong>
                </p>

                <p class="mb-2 text-lg text-slate-300">
                    Correct answer: <strong>{{ currentQuestion?.correctAnswer }}</strong>
                </p>

                <p class="mb-4 text-sm text-slate-300">
                    {{ currentQuestion?.explanation }}
                </p>

                <!-- This button moves user to the next question -->
                <button @click="nextQuestion"
                    class="mt-5 rounded-xl bg-cyan-500 px-5 py-3 font-medium text-slate-950 transition hover:bg-cyan-400">
                    {{ isLastQuestion ? 'Finish quiz' : 'Next question' }}
                </button>
            </div>
        </section>

        <section v-if="quizFinished" class="mt-6 rounded-2xl border border-slate-800 bg-slate-900 p-6">
            <h2 class="mb-2 text-2xl font-bold">
                Quiz complete
            </h2>

            <p class="text-slate-300">
                You scored {{ score }} out of {{ questions.length }}.
            </p>

            <!-- Button for resetting quiz -->
            <button @click="restartQuiz"
                class="mt-5 rounded-xl bg-cyan-500 px-5 py-3 font-medium text-slate-950 transition hover:bg-cyan-400">
                Try again
            </button>
        </section>
    </main>
</template>

<script setup lang="ts">
//questionText contains the question 
//correctAnswer has the correct answer among the choices
//explanation has the justification for the correct answer
type Question = {
    questionText: string
    choices: string[]
    correctAnswer: string
    explanation: string
}

// First 12 questions: Module 1
// Next 10 questions: Module 2
// Next 3 questions: Module 3
// Next ? questions: Module 4
// Next ? questions: Module 5
// Last ? questions: Module 6
let questions: Question[] = [
    {
        questionText: "Why is information security essential?",
        choices: [
            "Information has certain characteristics, that when violated, becomes no longer useful.",
            "It allows information to be shared freely without restriction.",
            "It guarantees that cyberattacks can never harm an organisation.",
            "It ensures that all employees have access to company information at all times.",
        ],
        correctAnswer: "Information has certain characteristics, that when violated, becomes no longer useful.",
        explanation: "Information has three properties: confidentiality, integrity and availability. When any of these are violated, the information becomes exposed to unintended users who could make the information unreliable and less accessible to the users who have the right to access it."
    },
    {
        questionText: "In cybersecurity, what does the letters in CIA stand for?",
        choices: [
            "Central, Intellligence, Agency",
            "Curiosity, Ingenuity, Advocacy",
            "Customisability, Identification, Accountability",
            "Confidentiality, Integrity, Availability",
        ],
        correctAnswer: "Confidentiality, Integrity, Accessbility",
        explanation: "CIA stands for confidentiality, integrity and accessbility, which are also the three properties of reliable information."
    },
    {
        questionText: "Which of these is NOT an additional goal for establishing security?",
        choices: ["Availability", "Authentication", "Accountability", "Authorisation"],
        correctAnswer: "Availability",
        explanation: "Availability is a necessary security goal. Authentication, accountability and authorisation are considered additional security goals."
    },
    {
        questionText: "Which of these additional security goals refers to the ability to recognise users who can access the information?",
        choices: ["Identification", "Authentication", "Authorisation", "Non-repudiation"],
        correctAnswer: "Identification",
        explanation: "Identification is the additional security goal that refers to the system's ability to recognise users and who has rightful access to the information."
    },
    {
        questionText: "Which of these additional security goals refers to the ability of the system to create irrefutable proof that a user has done a certain activity to the information?",
        choices: ["Identification", "Accountability", "Authorisation", "Non-repudiation"],
        correctAnswer: "Non-repudiation",
        explanation: "Non-repudiation refers to creating irrefutable proof that the activity occurred and the user has done it."
    },
    {
        questionText: "A law student hacked into the university's system to change their marks. In this situation, which security goal is compromised?",
        choices: ["Confidentiality", "Integrity", "Availability", "None"],
        correctAnswer: "Integrity",
        explanation: "Since the student gained unauthorised access to the system to modify their grades, integrity is violated."
    },
    {
        questionText: "A file that contained personal information and medical details of blood donors was posted on a public website. Which security goal was violated as a result?",
        choices: ["Confidentiality", "Integrity", "Availability", "All three"],
        correctAnswer: "Confidentiality",
        explanation: "As information is disclosed to other users when the file containing personal details is published, confidentiality was compromised."
    },
    {
        questionText: "Due to an outage, payment systems at self-service checkouts in some retail stores were unable to be used. Because of this, which security goal was violated?",
        choices: ["Confidentiality", "Integrity", "Availability", "Authorisation"],
        correctAnswer: "Availability",
        explanation: "Because payment systems were not available due to the outage, the availability of those systems were tampered with."
    },
    {
        questionText: "Encryption, access controls and over-provisioning are examples of which kind of control measure?",
        choices: ["Preventive", "Detective", "Corrective", "Confidentiality"],
        correctAnswer: "Preventive",
        explanation: "Encryption, access controls and over-provisioning are preventive controls as they prevent cyberattacks in some form."
    },
    {
        questionText: "Monitoring and intrusion detection systems are examples of which kind of control measure?",
        choices: ["Preventive", "Detective", "Corrective", "Monitoring"],
        correctAnswer: "Detective",
        explanation: "Both monitoring and intrusion detection systems check for unauthorised actions, therefore they are detective measures."
    },
    {
        questionText: "Backup records and system restores are examples of which kind of control measure?",
        choices: ["Preventive", "Detective", "Corrective", "Defective"],
        correctAnswer: "Corrective",
        explanation: "Backup records and system restores bring back the compromised systems or access to information assets so these are corrective measures."
    },
    {
        questionText: "Which of these statements are incorrect?",
        choices: [
            "Passive attacks usually violate the security goal of accessibility.",
            "Attackers commit an active attack when they modify, falsify or copy the information.",
            "It is usually hard to detect passive attacks.",
            "A security incident or attack is damaging if at least one of the security goals of an information asset is violated."
        ],
        correctAnswer: "Passive attacks usually violate the security goal of accessibility.",
        explanation: "Passive attacks occur when an attacker gains access to information they are not meant to view or listen to. Since passive attacks happen when attacker does not modify the information asset the security goal they usually violate is confidentiality."
    },
    {
        questionText: "What is the difference between passive and active attacks?",
        choices: [
            "Passive attacks happen when the attacker gains access to information they are not meant to access while active attacks happen attacker modifies, falsifies or destroys information.",
            "Passive attacks prevent authorized users from accessing information, while active attacks secretly monitor communications.",
            "Passive attacks encrypt information, while active attacks decrypt it without permission.",
            "Passive attacks focus on stealing passwords, while active attacks focus on deleting files."
        ],
        correctAnswer: "Passive attacks happen when the attacker gains access to information they are not meant to access while active attacks happen attacker modifies, falsifies or destroys information.",
        explanation: "Passive attacks involve observing or intercepting information without making any changes to it. Active attacks alter information or systems, often causing damage to the assets, files or systems. This makes the latter easier to detect."
    },
    {
        questionText: "Which of these is a passive attack?",
        choices: ["Eavesdropping", "Distributed denial of service (DDoS)", "Spoofing", "Phishing"],
        correctAnswer: "Eavesdropping",
        explanation: "Eavesdropping happens when an attacker listens to other people's conversations without their consent. As no information is altered in this attack, this is a passive attack."
    },
    {
        questionText: "Which of these is an active attack?",
        choices: ["Wiretapping", "Shoulder surfing", "Network monitoring", "Denial of service (DoS)"],
        correctAnswer: "Denial of service (DoS)",
        explanation: "A denial of service (DoS) attack prevents authorised users from accessing the information that they have permission for. Even if information is not altered during the attack, it still tampers with the system's availability which is detectable, therefore DoS is an active attack."
    },
    {
        questionText: "Which of these series of attacks are all active attacks?",
        choices: [
            "Man in the middle (MITM), replay attack, spoofing", 
            "Pharming, phishing, cyberbullying", 
            "Eavesdropping, shoulder surfing, network monitoring", 
            "Distributed denial of service (DDoS), man in the middle (MITM), packet sniffing"
        ],
        correctAnswer: "Man in the middle (MITM), replay attack, spoofing",
        explanation: "Man in the middle (MITM), replay attack and spoofing are all active attacks since they modify information in some way."
    },
    {
        questionText: "Which of these refer to a cyberattack that combines spoofing and social engineering?",
        choices: ["Phishing", "Pharming", "Spoofing", "Ransomware"],
        correctAnswer: "Phishing",
        explanation: "Phishing is a method that combines spoofing and social engineering. It involves the attacker starting communication with their victim while pretending to be an authorised entity."
    },
    {
        questionText: "Which of these refer to the attack that involves tapping into the network to gain knowledge of confidential information?",
        choices: ["Network monitoring", "Networking", "Session hijacking", "Packet injection"],
        correctAnswer: "Network monitoring",
        explanation: "Network monitoring is when attackers tap into the network to gain knowledge of confidential information."
    },
    {
        questionText: "Which of these refer to an attack where attackers insert a script in a database in order to alter the information stored in it?",
        choices: ["Man in the middle (MITM)", "Cross-site scripting (XSS)", "SQL injection", "Denial of service (DoS)"],
        correctAnswer: "SQL injection",
        explanation: "SQL injection is an attack that involves inserting malicious SQL scripts to alter information in a target database."
    },
    {
        questionText: "What is a replay attack?",
        choices: [
            "An attack involving repeatedly guessing passwords until the correct one is found.", 
            "An attack where an attacker intercepts a conversation and changes the messages before forwarding them to each party",
            "An attack where an attacker replays multiple requests to make a server unavailable",
            "An attack where an attacker records valid credentials in order to use that information later to gain access to a user's account or information they have access to."
        ],
        correctAnswer: "An attack where an attacker records valid credentials in order to use that information later to gain access to a user's account or information they have access to.",
        explanation: "A replay attack happens when an attacker captures a legitimate transmission and retransmits it later to trick a system into accepting it as authentic."
    },
    {
        questionText: "Which of these analogies are correct?",
        choices: [
            "Cross-site scripting : active attack ; Eavesdropping : passive attack",
            "Active attack : network monitoring ; Passive attack : social engineering",
            "Cross-site scripting : databases ; SQL injection : websites",
            "Phishing : emails ; Pharming : telephone lines"
        ],
        correctAnswer: "Cross-site scripting : active attack ; Eavesdropping : passive attack",
        explanation: "Cross-site scripting is an example of an active attack while eavesdropping is an example of a passive attack."
    },
    {
        questionText: "In information security, what is risk?",
        choices: [
            "The potential for loss or damage when a threat exploits a vulnerability", 
            "A software flaw that allows unauthorised access",
            "The possibility for loss of funds or other important assets",
            "An event that always results in a security breach"
        ],
        correctAnswer: "The potential for loss or damage when a threat exploits a vulnerability",
        explanation: "Risk is the possibility that a threat will exploit a vulnerability and cause harm to an organisation's information or systems. It considers both the likelihood of the event occurring and the potential impact if it does."
    },
    {
        questionText: "In information security, how is risk best managed?",
        choices: [
            "By eliminating all vulnerabilities from the system",
            "By avoiding the use of computers and the internet altogether",
            "By ignoring low-risk threats until they become serious incidents",
            "By involving all concerned parties and ensuring that it is managed according to the organisation's goals"
        ],
        correctAnswer: "By involving all concerned parties and ensuring that it is managed according to the organisation's goals",
        explanation: "Risk is best managed when involving all parties who should be concerned about it. It must also support the organisation's goals. It is also crucial for all parties involved to have a clear risk appetite, risk acceptance criteria and risk owners who can take accountability."
    },
    {
        questionText: "Which of these incorrectly describes a risk statement?",
        choices: [
            "A risk statement briefly explains risks to stakeholders.",
            "A risk statement can use if-then statements.",
            "A risk statement must convey the incident likely to happen, its consequences and the impact it will have to stakeholders or the business.",
            "A risk statement records every cyberattack that has occurred in a system."
        ],
        correctAnswer: "A risk statement records every cyberattack that has occurred in a system.",
        explanation: "Risk statements do not detail every possible attack that could happen. It only conveys one possible incident, its consequences and the impact it will have on the business and affected parties."
    },
    {
        questionText: "Which of these statements are incorrect?",
        choices: [
            "Security management frameworks are a set of software tools used to automatically detect and block all cybersecurity threats.",
            "Security management frameworks are provide a structured management of information security for companies and organisations.",
            "Security management frameworks offer a starting point for organisations that do not have information management or have a disorganised information management.",
            "Security management frameworks are used to plan information security in the workplace."
        ],
        correctAnswer: "Security management frameworks are a set of software tools used to automatically detect and block all cybersecurity threats.",
        explanation: "Ssecurity management frameworks provide a structured management of information security for companies and organisations. They are not software tools but are a set of documents that provide a structure for how to manage attacks and risk."
    },
    {
        questionText: "Which of these frameworks contains the requirements for implementing an Information Security Management System (ISMS)?",
        choices: [
            "ISO 27001",
            "NIST Cybersecurity Framework",
            "Cloud Security Alliance Cloud Controls Matrix",
            "Secure Controls Framework (SCF)"
        ],
        correctAnswer: "ISO 27001",
        explanation: "ISO 27001 contains the requirements for implementing an Information Security Management Systems (ISMS). It aims to align risk management with the organisation's so it is suitable for any organisation."
    },
    {
        questionText: "Which of these is NOT true about the NIST Cybersecurity Framework?",
        choices: [
            "Because this framework was made by a government, the framework is only compatible with governments.",
            "The NIST Framework is free to use.",
            "It comes with special publications to allow the organisation to customise their own information security program.",
            "The NIST Framework is frequently reviewed by industry professionals."
        ],
        correctAnswer: "Because this framework was made by a government, the framework is only compatible with governments.",
        explanation: "While the NIST Framework was made by the US Government, it is suitable for all kinds of industries."
    },
    {
        questionText: "Which of these is a disadvantage of ISO 27002?",
        choices: [
            "It does not cover technology-based controls.",
            "It requires an information security professional to apply it.",
            "It can only be used by organisations in the tech industry.",
            "The framework is only updated once every 5 years."
        ],
        correctAnswer: "It requires an information security professional to apply it.",
        explanation: "ISO 27002 requires an information security professional to apply it since implementation of the controls are difficult to understand."
    },
    {
        questionText: "Which of these is both a security management framework and a security controls framework?",
        choices: [
            "ISO 27001",
            "IS0 27002",
            "NIST Cybersecurity Framework",
            "Secure Controls Framework (SCF)"
        ],
        correctAnswer: "ISO 27002",
        explanation: "While it is mainly a security controls framework, ISO 27002 supports security management frameworks. In fact, it pairs well with ISO 27001, a security management framework."
    },
    {
        questionText: "Which of these best describes a Secure Controls Framework (SCF)?",
        choices: [
            "The SCF is a list of about 750 catalogued controls that allows businesses to create and maintain secure processes and systems.",
            "The SCF is a controls management framework for cloud service providers.",
            "The SCF was designed by the US Government and is free to use.",
            "The SCF is often used in UK and Australia."
        ],
        correctAnswer: "The SCF is a list of about 750 catalogued controls that allows businesses to create and maintain secure processes and systems.",
        explanation: "Designed by information security and privacy professionals, the SCF is a list of about 750 catalogued controls that allows businesses to create and maintain secure processes and systems."
    },
    {
        questionText: "",
        choices: [
            "",
            "",
            "",
            ""
        ],
        correctAnswer: "",
        explanation: ""
    },
    {
        questionText: "",
        choices: [
            "",
            "",
            "",
            ""
        ],
        correctAnswer: "",
        explanation: ""
    },
    {
        questionText: "",
        choices: [
            "",
            "",
            "",
            ""
        ],
        correctAnswer: "",
        explanation: ""
    },
    {
        questionText: "",
        choices: [
            "",
            "",
            "",
            ""
        ],
        correctAnswer: "",
        explanation: ""
    },
    {
        questionText: "",
        choices: [
            "",
            "",
            "",
            ""
        ],
        correctAnswer: "",
        explanation: ""
    },
    {
        questionText: "",
        choices: [
            "",
            "",
            "",
            ""
        ],
        correctAnswer: "",
        explanation: ""
    },
    {
        questionText: "",
        choices: [
            "",
            "",
            "",
            ""
        ],
        correctAnswer: "",
        explanation: ""
    },
    {
        questionText: "",
        choices: [
            "",
            "",
            "",
            ""
        ],
        correctAnswer: "",
        explanation: ""
    },
    {
        questionText: "",
        choices: [
            "",
            "",
            "",
            ""
        ],
        correctAnswer: "",
        explanation: ""
    },
    {
        questionText: "",
        choices: [
            "",
            "",
            "",
            ""
        ],
        correctAnswer: "",
        explanation: ""
    },
    {
        questionText: "",
        choices: [
            "",
            "",
            "",
            ""
        ],
        correctAnswer: "",
        explanation: ""
    },
    {
        questionText: "",
        choices: [
            "",
            "",
            "",
            ""
        ],
        correctAnswer: "",
        explanation: ""
    },
    {
        questionText: "",
        choices: [
            "",
            "",
            "",
            ""
        ],
        correctAnswer: "",
        explanation: ""
    },
    {
        questionText: "",
        choices: [
            "",
            "",
            "",
            ""
        ],
        correctAnswer: "",
        explanation: ""
    },
    {
        questionText: "",
        choices: [
            "",
            "",
            "",
            ""
        ],
        correctAnswer: "",
        explanation: ""
    },
]

//TODO: adjust question limit and pass percentage
const maxQuestions = 10
const passPercentage = 0.7
const minCorrectAnswers = Math.round(maxQuestions * passPercentage)

//shuffle questions 
const shuffledQuestions = [...questions].sort(() => Math.random() - 0.5)
questions = shuffledQuestions

const currentQuestionIndex = ref(0) // get current question number
const selectedAnswer = ref<string | null>(null) // gets user's answer 
const score = ref(0) // get user's score 
const quizFinished = ref(false) //check if quiz is finished

const currentQuestion = computed(() => questions[currentQuestionIndex.value]) //get current question

//shuffle choices in currentQuestion and put it in a ref 
const currentChoices = computed(() => {
    return [...(currentQuestion.value?.choices ?? [])]
        .sort(() => Math.random() - 0.5)
})

const hasAnswered = computed(() => selectedAnswer.value !== null) //check if user has answered 

//compares user's answers to correct answer of current question
const isCorrect = computed(() => {
    return selectedAnswer.value === currentQuestion.value?.correctAnswer
})

//checks if user is at last question to finish the quiz
const isLastQuestion = computed(() => {
    return maxQuestions === questions.length - 1
})

//record user's answer and add 1 to user's score if user got it right 
function answerQuestion(answer: string) {
    selectedAnswer.value = answer

    if (answer === currentQuestion.value?.correctAnswer) {
        score.value++
    }
}

//increment quiz question index by 1 unless quiz is at last question 
//after moving to next question, reset user's selected answer to null 
function nextQuestion() {
    if (isLastQuestion.value) {
        quizFinished.value = true
        return
    }

    currentQuestionIndex.value++
    selectedAnswer.value = null
}

//reset all values and allow user to take the quiz again 
function restartQuiz() {
    currentQuestionIndex.value = 0
    selectedAnswer.value = null
    score.value = 0
    quizFinished.value = false
}
</script>