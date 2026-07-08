<script setup lang="ts">
const sections = [
    {
        id: '0',
        title: 'What is penetration testing?',
    },
    {
        id: '1',
        title: 'Types of pen testing',
    },
    {
        id: '2',
        title: 'Typical pen testing steps',
    },
    {
        id: '3',
        title: 'Initial engagement',
    },
    {
        id: '4',
        title: 'Scoping',
    },
    {
        id: '5',
        title: 'Testing',
    },
    {
        id: '6',
        title: 'Reporting',
    },
    {
        id: '7',
        title: 'Following up',
    },
    {
        id: '9',
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
                    Information Security Management: Module 6
                </p>

                <h1 class="mb-4 text-4xl font-bold">
                    Penetration Testing
                </h1>

                <p class="mb-8 text-slate-300">
                    Learn the concepts and fundamentals of pen testing.
                </p>

                <div class="mb-10 rounded-2xl border border-slate-800 bg-slate-900 p-5">
                    <p class="text-sm text-slate-400">Estimated reading time</p>
                    <p class="mt-1 text-lg font-semibold">12 minutes</p>
                </div>

                <section id="0" class="scroll-mt-24 border-b border-slate-800 pb-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        What is penetration testing?
                    </h2>

                    <p class="mb-4 text-slate-300">
                        Penetration testing, simply known as pen testing, is a manually executed, offensive
                        cybersecurity test conducted
                        by an organisation to identify existing vulnerabilities and flaws in a information system's
                        security.
                        This is done so that the existing security's threat detection and response can be improved.
                        They are also a point-in-time assessment, so they only identify vulnerabilities when the test is
                        conducted.
                    </p>
                </section>

                <section id="1" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Types of pen testing
                    </h2>

                    <p class="mb-4 text-slate-300">
                        In <strong>whitebox testing</strong>, the conductors of the test have complete information of
                        the system. It is often conducted to validate how effective a control is against threats and
                        vulnerabilties.
                    </p>
                    <p class="mb-4 text-slate-300">
                        In <strong>blackbox testing</strong>, the conductors of the test do not know what the system
                        does. It is often used to simulate actual cyberattacks. However, this method may not allow all
                        vulnerabilities to be identified in the test.
                    </p>
                    <p class="mb-4 text-slate-300">
                        One reason why these tests are conducted is to identify vulnerabilities in a niche web or mobile
                        application.
                        The findings should also supply essential feedback to improve developers' coding practices.
                        Another one could be to conduct scenario-driven testing to identify vulnerabilities that could
                        emerge from it. Simulating such tests with actual incident data can be useful to inform
                        scenarios and prepare the system for a similar situation.
                        It could also be done to test incident detection and response times, which can be performed with
                        responders being aware of what will happen or as tests where responders will not know how the
                        system's security will be attacked.
                    </p>
                </section>

                <section id="2" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Typical pen testing steps
                    </h2>

                    <ol class="mb-4 list-decimal space-y-3 pl-6 text-slate-300">
                        <li>Initial engagement</li>
                        <li>Scoping</li>
                        <li>Testing</li>
                        <li>Reporting</li>
                        <li>Following up</li>
                    </ol>
                </section>

                <section id="3" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Initial engagement
                    </h2>

                    <p class="mb-4 text-slate-300">
                        According to Rhodes, the conductors of the test must have the right skills and have the proper
                        experience to execute it.
                        The requirements and the context of the test have to clearly specified, especially for uncommon
                        or complex systems like SAP.
                    </p>
                </section>

                <section id="4" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Scoping
                    </h2>

                    <p class="mb-4 text-slate-300">
                        In this step, all stakeholders involved need to be identified. This includes risk owners,
                        service owners, technical staff and at least one person who can conduct the pen test.
                    </p>
                    <p class="mb-4 text-slate-300">
                        Each participant must contribute to the scope discussion.
                    </p>
                    <ol class="mb-4 list-disc space-y-3 pl-6 text-slate-300">
                        <li>Risk and service owners should highlight areas of concern</li>
                        <li>Technical staff should outline the technical boundaries of the system to be tested</li>
                        <li>The pen test team should identify the type of testing to use to get a complete idea of the
                            vulnerability of the target</li>
                    </ol>
                    <p class="mb-4 text-slate-300">
                        Specific times when testing should happen and systems excluded from testing should be addressed
                        and confirmed.
                        Systems that have to be tested in a particular way should also be addressed.
                    </p>
                    <p class="mb-4 text-slate-300">
                        The discussion must produce an output in the form of an engagement plan, which should include
                    </p>
                    <ol class="mb-4 list-disc space-y-3 pl-6 text-slate-300">
                        <li>Boundaries of testing, both technical and physical</li>
                        <li>Types of testing that will be conducted</li>
                        <li>Time frame and time constraints on testing and reporting</li>
                        <li>Needs of the pen test team</li>
                        <li>Compliance requirements</li>
                        <li>Reporting requirements</li>
                    </ol>
                </section>

                <section id="5" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Testing
                    </h2>

                    <p class="mb-4 text-slate-300">
                        This is the stage where testing is executed by the team. There are some important aspects to
                        take note of while testing.
                    </p>

                    <ol class="mb-4 list-disc space-y-3 pl-6 text-slate-300">
                        <li>The pen test team and the client should remain in communication, in case testing goes wrong
                            and affects other systems</li>
                        <li>Test team should know how to escalate critical issues</li>
                        <li>Barriers to effective testing must be reported and resolved as soon as possible</li>
                        <li>Changes in scope should be acknowledged by all parties, and these changes should be resolved
                            and recorded</li>
                    </ol>
                </section>

                <section id="6" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Reporting
                    </h2>

                    <p class="mb-4 text-slate-300">
                        A draft is sent and reviewed by the most important stakeholders before a report is produced.
                        In this phase, the pen test team needs to be level-headed and diplomatic, so they should not
                        blame people.
                        Collaboration and maintaining positivity is important to obtain the best results for the report.
                    </p>
                </section>

                <section id="7" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Following up
                    </h2>

                    <p class="mb-4 text-slate-300">
                        The pen test report is required to analysed so that it aligns with the organisational context,
                        the organisation's objectives and the business' impacts. Afterwards, treatment plans can be
                        created based on these findings.
                    </p>
                </section>

                <section id="9" class="scroll-mt-24 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Sources
                    </h2>

                    <div class="space-y-3">
                        <div class="rounded-xl border border-slate-800 bg-slate-900 p-4">
                            Rhodes, A. (2023). <em>IFN541 Information Security Management: Vulnerability
                                Management.</em> [Presentation]. <a class="text-cyan-400"
                                href="https://www.canvas.qut.edu.au/">Canvas.</a>
                        </div>
                    </div>
                </section>

                <section id="10" class="flex gap-4 px-8 py-10 rounded-xl border border-slate-800 bg-slate-900">
                    <div class="flex flex-col gap-1">
                        <h2 class="text-2xl font-semibold">
                            Midpoint Assessment
                        </h2>
                        <p class="text-white">See how much you know about <strong>Modules 1-6 of Information Security Management</strong> so far.</p>
                    </div>

                    <div class="flex ml-auto text-center">
                        <NuxtLink to="/assessments/infosec-mgmt/assessment1"
                            class="rounded-xl bg-cyan-500 my-4 px-5 py-3 font-semibold text-slate-950 hover:bg-cyan-400 h-[50px] w-[120px]">
                            Take Test
                        </NuxtLink>
                    </div>
                </section>

                <div class="mt-10 flex justify-between border-t border-slate-800 pt-6">
                    <NuxtLink to="/courses/infosec-mgmt/module5"
                        class="rounded-xl border border-slate-700 px-5 py-3 text-sm text-slate-300 hover:bg-slate-800">
                        Previous
                    </NuxtLink>

                    <SelectInfoSec />

                    <NuxtLink to="/courses/infosec-mgmt/module6"
                        class="rounded-xl bg-cyan-500 px-5 py-3 text-sm font-semibold text-slate-950 hover:bg-cyan-400">
                        Next
                    </NuxtLink>
                </div>
            </article>

            <CoursesSidebar :sections="sections" />
        </section>
    </main>
</template>