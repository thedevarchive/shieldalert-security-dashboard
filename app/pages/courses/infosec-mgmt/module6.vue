<script setup lang="ts">
const sections = [
    {
        id: '0',
        title: '',
    },
    {
        id: '1',
        title: '',
    },
    {
        id: '2',
        title: '',
    },
    {
        id: '3',
        title: '',
    },
    {
        id: '4',
        title: '',
    },
    {
        id: '5',
        title: '',
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
                        The vulnerability management process
                    </h2>

                    <ol class="mb-4 space-y-3 pl-6 text-slate-300">
                        <li>Maintaining an asset inventory (both hardware and software)</li>
                        <li>Establishing secure configurations</li>
                        <li>Maintaining awareness of new vulnerabilties and detecting them</li>
                        <li>Mitigating and remediating identified vulnerabilities</li>
                        <li>Continuously monitorign the organisation's environment</li>
                    </ol>
                </section>

                <section id="3" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Common Vulnerability Scoring System (CVSS)
                    </h2>

                    <p class="mb-4 text-slate-300">
                        This framework was created by the non-profit organisation Forum of Incident Response and
                        Security Teams (FIRST) to characterise and classifies these vulnerabilities.
                        The system has two sets of base metrics: exploitability and impact. However, the CVSS base
                        impacts do not consider organisational impact.
                        The results of the scoring system ranges from 0 to 10.
                    </p>
                </section>

                <section id="4" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Common Vulnerabilities and Exposures (CVE)
                    </h2>

                    <p class="mb-4 text-slate-300">
                        Created and maintained by MITRE, this is a public list of cybersecurity vulnerabilities.
                        They also set the standards for naming the software vulnerabilities.
                    </p>
                </section>

                <section id="5" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        The US National Vulnerability Database (NVD)
                    </h2>

                    <p class="mb-4 text-slate-300">
                        This database is created by NIST and contains CVE-identified software vulnerabilities.
                        It also has advanced search features that allow users to search by product name, version and
                        even search by vulnerability type and severity.
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

                <div class="mt-10 flex justify-between border-t border-slate-800 pt-6">
                    <NuxtLink to="/courses/infosec-mgmt/module4"
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