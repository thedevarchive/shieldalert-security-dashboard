<template>
    <AssessmentQuiz
        course-title="Information Security Management"
        assessment-title="Midpoint Assessment"
        :instructions="instructions"
        :questions="questions"
        :max-questions="30"
        :pass-percentage="0.7"
    />
</template>

<script setup lang="ts">
import type { AssessmentQuestion } from '~/types/assessment'

const instructions = [
    'Read each question carefully and select the best answer from the provided options.',
    'Please allow 30 minutes of your time to complete the test. However, you will not be timed.',
    'You must correctly answer 70% of the questions to pass the test.',
]

// First 12 questions: Module 1
// Next 10 questions: Module 2
// Next 3 questions: Module 3
// Next 6 questions: Module 4
// Next 10 questions: Module 5
// Last 8 questions: Module 6
const questions: AssessmentQuestion[] = [
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
        correctAnswer: "Confidentiality, Integrity, Availability",
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
            "ISO 27002",
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
        questionText: "Which of these kinds of documents are NOT created by CIS?",
        choices: [
            "Controls",
            "Benchmarks",
            "Hardened images",
            "Security management"
        ],
        correctAnswer: "Security management",
        explanation: "The Center for Internet Security (CIS) does not have a general security management framework, but it has created CIS Controls, CIS Benchmarks and CIS Hardened Images."
    },
    {
        questionText: "Why is vulnerability management important?",
        choices: [
            "Reducing vulnerabilities is the best way to lower risk and mitigate chances of attackers exploiting the system.",
            "It helps organisations identify and eliminate all threats before they can target a system.",
            "Reducing attackers before vulnerabilities are discovered is the best way to lower risk.",
            "It helps organisations identify vulnerabilities only after they have been exploited."
        ],
        correctAnswer: "Reducing vulnerabilities is the best way to lower risk and mitigate chances of attackers exploiting the system.",
        explanation: "Proactively reducing risk before they happen is the goal of vulnerability management. The main way risk is reducing risk is through reducing the vulnerabilities attackers can exploit."
    },
    {
        questionText: "Which of these is NOT a common information security vulnerability?",
        choices: [
            "Flaws in the design and testing of technology",
            "Lack of rules or gaps in business policies or processes",
            "Lack of user training and awareness",
            "Lack of user experience and technical skills"
        ],
        correctAnswer: "Lack of user experience and technical skills",
        explanation: "A user's inexperience with information security or technical skills is not a common information security vulnerability. However, an organisation's lack of user training and user awareness on information security is."
    },
    {
        questionText: "Which of these is NOT a vulnerability management process?",
        choices: [
            "Maintaining asset inventories for hardware and software",
            "Monitoring the organisation's environment continuously",
            "Mitigating and remediating identified vulnerabilities",
            "Maintaining backups of critical organisational information"
        ],
        correctAnswer: "Maintaining backups of critical organisational information",
        explanation: "Maintaining backups of critical organisational information is not a necessary step to fulfil, but the other choices are part of the process."
    },
    {
        questionText: "Which one of these refers to a public list of cybersecurity vulnerabilities?",
        choices: [
            "Common Vulnerability Scoring System (CVSS)",
            "Common Vulnerabilities and Exposures (CVE)",
            "The US National Vulnerability Database (NVD)",
            "National Institute of Standards and Technology (NIST)"
        ],
        correctAnswer: "Common Vulnerabilities and Exposures (CVE)",
        explanation: "The CVE is a public list of cybersecurity vulnerabilities created and maintained by MITRE."
    },
    {
        questionText: "Which of these is NOT true about the Common Vulnerability Scoring System (CVSS)?",
        choices: [
            "The framework was created by FIRST.",
            "The CVSS has three metrics: base, temporal and environmental.",
            "Base impacts cover organisational impact.",
            "The results of the scoring system ranges from 0 to 10."
        ],
        correctAnswer: "Base impacts cover organisational impact.",
        explanation: "In the CVSS, the impact metric under the base metric does not cover organisational impact. However, the enviromental metric covers it."
    },
    {
        questionText: "Which of these have advanced search features that allow users to search by product name, version, vulnerability type and severity?",
        choices: [
            "Common Vulnerability Scoring System (CVSS)",
            "Common Vulnerabilities and Exposures (CVE)",
            "The US National Vulnerability Database (NVD)",
            "National Institute of Standards and Technology (NIST)"
        ],
        correctAnswer: "The US National Vulnerability Database (NVD)",
        explanation: "The US National Vulnerability Database (NVD) has advanced search features that allow users to search by product name, version and even search by vulnerability type and severity."
    },
    {
        questionText: "Which of these analogies are correct?",
        choices: [
            "CVE : Scoring ; NVD : Database",
            "Base : Organisational impact ; Impact : Confidentiality impact",
            "Establishing secure configurations : Hardening ; Detecting vulnerabilities : VM tools",
            "CVSS : NIST ; NVD : FIRST"
        ],
        correctAnswer: "Establishing secure configurations : Hardening ; Detecting vulnerabilities : VM tools",
        explanation: "Both of these refer to different vulnerability management processes. Establishing secure configurations is the step that determines which controls should be hardened while detecting vulnerabilities involves using VM tools."
    },
    {
        questionText: "Which of these is NOT an important question to ask pertaining to maintaining an asset inventory?",
        choices: [
            "Is the asset vendor still supported?",
            "What is the asset's current patch status?",
            "What is the asset's current configuration?",
            "Should the asset be discontinued?"
        ],
        correctAnswer: "Should the asset be discontinued?",
        explanation: "\"Should the asset be discontinued?\" is not an important question for asset inventory. It may reduce the attack surface, but if the organisation requires that asset, this is not a necesary question to ask."
    },
    {
        questionText: "Which of these processes refers to deciding which assets or configurations of an asset should be hardened and how?",
        choices: [
            "Establishing secure configurations",
            "Maintaining awareness and detecting vulnerabilities",
            "Mitigating and remediating identified vulnerabilities",
            "Continuously monitoring the environment"
        ],
        correctAnswer: "Establishing secure configurations",
        explanation: "The process of establishing secure configurations involving planning which assets or configurations to harden and how they should be done."
    },
    {
        questionText: "In the vulnerability management process, what is done to maintain awareness and detect vulnerabilities?",
        choices: [
            "Usage of vulnerability management (VM) tools to identify new vulnerabilities",
            "Hardening configurations",
            "Identifying assets that need to be secured",
            "Applying patches to improve security"
        ],
        correctAnswer: "Usage of vulnerability management (VM) tools to identify new vulnerabilities",
        explanation: "Maintaining awareness and detecting vulnerabilities involves being aware of vulnerabilities, and VM tools help ease the process of finding and summarising such information."
    },
    {
        questionText: "Which one of these does NOT answer the question \"Why do changes in the asset's or system's environment need to be identified often?\"",
        choices: [
            "Old vulnerabilities will automatically be removed as a result.",
            "New systems get installed.",
            "New vulnerabilities will be found from time to time.",
            "Old vulnerabilities that had temporary fixes can still be exploited."
        ],
        correctAnswer: "Old vulnerabilities will automatically be removed as a result.",
        explanation: "Old vulnerabilities will not immediately resolve after monitoring the environment. In fact, they are still likely to be exploited by attackers especially if they were temporarily patched."
    },
    {
        questionText: "Which of these is NOT true about penetration testing?",
        choices: [
            "Pen testing is an offensive cybersecurity test done to identify existing vulnerabilities and flaws in a information system's security.",
            "Pen testing is conducted to improve the existing security's threat detection and response.",
            "Pen testing is a point-in-time assessment.",
            "Pen testing needs to be only done once."
        ],
        correctAnswer: "Pen testing needs to be only done once.",
        explanation: "As pen testing is a point-in-time assessment, it can only identify the current vulnerabilities that exist in the system. It is highly recommend that it needs to be done more than once, and at regular intervals, to keep security up-to-date."
    },
    {
        questionText: "Which type of pen testing provides the testers with complete information of system?",
        choices: [
            "Whitebox testing",
            "Blackbox testing",
            "Greybox testing",
            "Redbox testing"
        ],
        correctAnswer: "Whitebox testing",
        explanation: "In whitebox testing, the conductors of the test have complete information of the system to validate the effectiveness of a control against threats and vulnerabilities."
    },
    {
        questionText: "Which type of pen testing is better used to simulate actual cyberattacks?",
        choices: [
            "Whitebox testing",
            "Blackbox testing",
            "Greybox testing",
            "Bluebox testing"
        ],
        correctAnswer: "Blackbox testing",
        explanation: "As blackbox testing have the testers not know what the system does, it is often used to simulate cyberattacks."
    },
    {
        questionText: "Which of these is the correct order of steps in pen testing?",
        choices: [
            "Initial engagement, scoping, testing, reporting, following up",
            "Initial engagement, testing, scoping, reporting, following up",
            "Initial engagement, testing, scoping, following up, reporting",
            "Initial engagement, reporting, scoping, testing, following up"
        ],
        correctAnswer: "Initial engagement, scoping, testing, reporting, following up",
        explanation: "The typical pen testing steps are in this order: initial engagement, scoping, testing, reporting and following up."
    },
    {
        questionText: "Why is initial engagement important in pen testing?",
        choices: [
            "It establishes the clearly specified requirements, context of the test and the testers who are qualified to execute it.",
            "It establishes the vulnerabilities and exploits that will be discovered during the penetration test.",
            "It allows penetration testers to begin exploiting systems before defining the scope of the test.",
            "It determines the final security controls that must be implemented after the pen test."
        ],
        correctAnswer: "It establishes the clearly specified requirements, context of the test and the testers who are qualified to execute it.",
        explanation: "In the initial engagement phase, the requirements and the context of the test have to clearly specified, especially for uncommon or complex systems. Moreover, the conductors of the test must have the right skills and have the proper experience to execute it."
    },
    {
        questionText: "Which is NOT true about the scoping phase in pen testing?",
        choices: [
            "Not all stakeholders need to be identified.",
            "Each participant must contribute to the scope discussion.",
            "Specific times when testing should happen and systems excluded from testing should be addressed and confirmed.",
            "The discussion must result in an engagement plan."
        ],
        correctAnswer: "Not all stakeholders need to be identified.",
        explanation: "In the scoping phase, all stakeholders need to be identified. This includes risk owners, service owners, technical staff and at least one person who can conduct the pen test."
    },
    {
        questionText: "Which of these is NOT true about the testing phase in pen testing?",
        choices: [
            "The pen test team and the client should remain in communication.",
            "Test team should know how to escalate critical issues.",
            "Barriers to effective testing must be reported and resolved as soon as possible.",
            "Changes in scope should be reserved for the next planned pen testing."
        ],
        correctAnswer: "Changes in scope should be reserved for the next planned pen testing.",
        explanation: "In the testing phase, changes in scope should be acknowledged by all parties, and these changes should be resolved and recorded."
    },
    {
        questionText: "Which pen testing step involves analysing a report so that it aligns with the organisational context?",
        choices: [
            "Initial engagement",
            "Scoping",
            "Reporting",
            "Following up"
        ],
        correctAnswer: "Following up",
        explanation: "Following up involves analysing the produced report in the reporting stage so that it aligns with the organisation's context, objectives and business impact."
    }
]
</script>
