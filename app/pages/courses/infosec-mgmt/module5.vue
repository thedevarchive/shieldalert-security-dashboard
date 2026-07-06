<script setup lang="ts">
const sections = [
    {
        id: '0',
        title: 'What is vulnerability management?',
    },
    {
        id: '1',
        title: 'Common information security vulnerabilities',
    },
    {
        id: '2',
        title: 'The vulnerability management process',
    },
    {
        id: '3',
        title: 'Common Vulnerability Scoring System (CVSS)',
    },
    {
        id: '4',
        title: 'Common Vulnerabilities and Exposures (CVE)',
    },
    {
        id: '5',
        title: 'The US National Vulnerability Database (NVD)',
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
                    Information Security Management: Module 5
                </p>

                <h1 class="mb-4 text-4xl font-bold">
                    Vulnerability Management
                </h1>

                <p class="mb-8 text-slate-300">
                    Learn about vulnerability management and some resources that ranks and lists these vulnerabilities.
                </p>

                <div class="mb-10 rounded-2xl border border-slate-800 bg-slate-900 p-5">
                    <p class="text-sm text-slate-400">Estimated reading time</p>
                    <p class="mt-1 text-lg font-semibold">18 minutes</p>
                </div>

                <section id="0" class="scroll-mt-24 border-b border-slate-800 pb-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        What is vulnerability management?
                    </h2>

                    <p class="mb-4 text-slate-300">
                        According to Rhodes, vulnerability management is a thorough process in order to continuously
                        maintain an organisation's vulnerabilities.
                        It is important because reducing vulnerabilities is the best way to lower risk and mitigate
                        chances of attackers exploiting the system.
                    </p>
                </section>

                <section id="1" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Common information security vulnerabilities
                    </h2>

                    <ul class="mb-4 list-disc space-y-3 pl-6 text-slate-300">
                        <li>Flaws in the design and testing of technology</li>
                        <li>Poor implementation of hardware or software</li>
                        <li>Lack of rules or gaps in business policies or processes</li>
                        <li>Lack of user training and awareness</li>
                        <li>Physical or environmental factors</li>
                    </ul>
                </section>

                <section id="2" class="scroll-mt-24 border-b border-slate-800 py-10">
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

                <section id="3" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Common Vulnerabilities and Exposures (CVE)
                    </h2>

                    <p class="mb-4 text-slate-300">
                        Created and maintained by MITRE, this is a public list of cybersecurity vulnerabilities.
                        They also set the standards for naming the software vulnerabilities.
                    </p>
                </section>

                <section id="4" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        The US National Vulnerability Database (NVD)
                    </h2>

                    <p class="mb-4 text-slate-300">
                        This database is created by NIST and contains CVE-identified software vulnerabilities.
                        It also has advanced search features that allow users to search by product name, version and
                        even search by vulnerability type and severity.
                    </p>
                </section>

                <section id="5" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        The vulnerability management process
                    </h2>

                    <ol class="mb-4 list-decimal space-y-3 pl-6 text-slate-300">
                        <li>Maintaining asset inventories for hardware and software</li>
                        <li>Establishing secure configurations</li>
                        <li>Maintaining awareness of new vulnerabilties and detecting them</li>
                        <li>Mitigating and remediating identified vulnerabilities</li>
                        <li>Continuously monitoring the organisation's environment</li>
                    </ol>
                </section>

                <section id="6" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Maintaining an asset inventory
                    </h2>

                    <p class="mb-4 text-slate-300">
                        Maintaining both a hardware and software inventory is the most essential step because it is
                        difficult to protect something you do not know.
                        Identifying the asset that needs protection, where it is and its current state must be done
                        first before vulnerability management can begin.
                    </p>
                    <p class="mb-4 text-slate-300">
                        Some important questions to ask are
                    </p>
                    <ol class="mb-4 list-decimal space-y-3 pl-6 text-slate-300">
                        <li>Is the asset vendor still supported?</li>
                        <li>What is the asset's current patch status?</li>
                        <li>What is the asset's current configuration?</li>
                    </ol>
                </section>

                <section id="7" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Establishing secure configurations
                    </h2>

                    <p class="mb-4 text-slate-300">
                        This phase is for establishing which configurations should be hardened and in what way should
                        they be done.
                        This helps reduce vulnerabilities and makes patching them easier.
                    </p>
                </section>

                <section id="8" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Maintaining awareness and detecting vulnerabilities
                    </h2>

                    <p class="mb-4 text-slate-300">
                        While being aware of vulnerabilities can be challenging since there is a lot of information on
                        them, vulnerability management tools can help since they provide a summary of the information
                        out there. They can also find vulnerabilities in assets as well. 
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