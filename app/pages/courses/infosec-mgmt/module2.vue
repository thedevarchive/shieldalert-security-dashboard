<script setup lang="ts">
const sections = [
    {
        id: '0',
        title: 'Security incidents and attacks',
    },
    {
        id: '1',
        title: 'Attack types',
    },
    {
        id: '2',
        title: 'Types of passive attacks',
    },
    {
        id: '3',
        title: 'Types of active attacks',
    },
    {
        id: '5',
        title: 'Sources',
    },
]
</script>

<template>
    <main class="min-h-screen bg-slate-950 text-white">
        <section class="mx-auto flex max-w-7xl gap-8 px-6 py-10">
            <article class="max-w-3xl flex-1">
                <NuxtLink to="/courses" class="mb-6 inline-block text-sm text-cyan-400 hover:text-cyan-300">
                    ← Back to courses
                </NuxtLink>

                <p class="mb-2 font-semibold text-cyan-400">
                    Information Security Management: Module 2
                </p>

                <h1 class="mb-4 text-4xl font-bold">
                    Security Incidents and Attacks
                </h1>

                <p class="mb-8 text-slate-300">
                    Learn about the different types of cyberattacks.
                </p>

                <div class="mb-10 rounded-2xl border border-slate-800 bg-slate-900 p-5">
                    <p class="text-sm text-slate-400">Estimated reading time</p>
                    <p class="mt-1 text-lg font-semibold">10 minutes</p>
                </div>

                <section id="0" class="scroll-mt-24 border-b border-slate-800 pb-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Security incidents and attacks
                    </h2>

                    <p class="mb-4 text-slate-300">
                        A security incident happens when a threat exploits a vulnerability and information assets are
                        impacted in the process.
                        Security incidents become considered "attacks" when human action is the cause.
                        Attackers are people who intentionally exploit vulnerabilities gain access to the assets in
                        question.
                        A security incident or attack is damaging if at least one of the security goals of an
                        information asset is violated.
                    </p>
                </section>

                <section id="1" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Attack types
                    </h2>

                    <p class="mb-4 text-slate-300">
                        There are two kinds of attacks: passive and active.
                    </p>

                    <p class="mb-4 text-slate-300">
                        In a passive attack, the attacker does not alter the asset. They only view or listen to the
                        asset.
                        Thus, it is hard to identify if this incident has occurred, and the most common security goal violated by this attack is confidentiality. 
                        Attackers commit an active attack when they modify, falsify or copy the information that they are not meant to access. 
                    </p>
                </section>

                <section id="2" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Types of passive attacks 
                    </h2>

                    <p class="mb-4 text-slate-300">
                        According to Liu, eavesdropping is listening to other people's conversations without their consent, and information is gathered from either the content or the people involved in the conversation.
                        Wiretapping is the act of eavesdropping over a telephone network, and is harder to detect in wireless networks. 
                    </p>

                    <p class="mb-4 text-slate-300">
                        Shoulder surfing is like eavesdropping but done with observation instead of listening; this is the act of looking at others' screens without consent. 
                        Attackers who commit shoulder surfing attempt to gain access to credentials such as a user's PIN or password, but could be use for other types of data such as a user's personal details. 
                    </p>

                    <p class="mb-4 text-slate-300">
                        Network monitoring is when attackers tap into the network to gain knowledge of confidential information. 
                    </p>
                </section>

                <section id="3" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Types of active attacks 
                    </h2>

                    <p class="mb-4 text-slate-300">
                        A denial of service (DoS) attack prevents authorised users from accessing the information that they have permission for. 
                        Attackers would corrupt the file, sever the communication between the user and the system or even crashing the service by sending many requests. 
                        A distributed denial of service (DDoS) works similarly, but multiple attackers or machines attempt make the system deny legitimate requests from authorised users. 
                    </p>

                    <p class="mb-4 text-slate-300">
                        Spoofing is when an attacker assumes to be a different entity in order to trick others into giving the attacker their information or credentials. 
                        Some common spoofing attacks are caller ID spoofing, email spoofing and webpage spoofing. 
                        Social engineering is when attackers simulate social situations to allow people to reveal information to them or let attackers access resources. 
                        They can claim to be someone they know, such as a family member or a coworker, and ask the victim for information. 
                    </p>

                    <p class="mb-4 text-slate-300">
                        Phishing is a method that combines spoofing and social engineering. 
                        It involves the attacker starting communication with their victim while pretending to be an authorised entity. 
                        They would also pressure the victim into acting on their communicated requests immediately either with a consequence or a reward. 
                        For example, an attacker would send an email pretending to be tech support and threaten the user to lock up their account if they do not fulfil a payment. 
                    </p>

                    <p class="mb-4 text-slate-300">
                        A man-in-the-middle (MITM) attack happens when an attacker intervenes in the middle of a conversation. 
                        The people in the conversation would believe that they are talking to one another, when in fact, the attacker is talking to both of them separately. 
                        In this way, the attacker seizes control of the conversation. 
                    </p>

                    <p class="mb-4 text-slate-300">
                        A replay attack happens when the attacker records a certain information or credential from an authorised user, and uses that information to allow the attacker to access it. 
                        The attacker may not know what the exact credentials are, and can simply record and replicate the encrypted value.  
                    </p>
                </section>

                <section id="5" class="scroll-mt-24 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Sources
                    </h2>

                    <div class="space-y-3">
                        <div class="rounded-xl border border-slate-800 bg-slate-900 p-4">
                            Liu, V. (2023). <em>IFN553 Introduction to Security and Networking: How Things Go Wrong,
                                Part B: Security Incidents and Attacks</em> [Presentation]. <a class="text-cyan-400"
                                href="https://www.canvas.qut.edu.au/">Canvas.</a>
                        </div>
                    </div>
                </section>

                <div class="mt-10 flex justify-between border-t border-slate-800 pt-6">
                    <NuxtLink to="/courses/infosec-mgmt/module1"
                        class="rounded-xl border border-slate-700 px-5 py-3 text-sm text-slate-300 hover:bg-slate-800">
                        Previous
                    </NuxtLink>

                    <SelectInfoSec />

                    <NuxtLink to="/courses/infosec-mgmt/module3"
                        class="rounded-xl bg-cyan-500 px-5 py-3 text-sm font-semibold text-slate-950 hover:bg-cyan-400">
                        Next
                    </NuxtLink>
                </div>
            </article>

            <CoursesSidebar :sections="sections" />
        </section>
    </main>
</template>