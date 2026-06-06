<script setup lang="ts">
import InfoSecSelect from '~/components/selects/InfoSecSelect.vue';

const sections = [
    {
        id: '0',
        title: 'What is risk?',
    },
    {
        id: '1',
        title: 'Creating risk statements',
    },
    {
        id: '2',
        title: 'Communicating risks',
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
                    Risk Management
                </h1>

                <p class="mb-8 text-slate-300">
                    Learn what risk is, how to express risk to others and how to make risk statements.
                </p>

                <div class="mb-10 rounded-2xl border border-slate-800 bg-slate-900 p-5">
                    <p class="text-sm text-slate-400">Estimated reading time</p>
                    <p class="mt-1 text-lg font-semibold">5 minutes</p>
                </div>

                <section id="0" class="scroll-mt-24 border-b border-slate-800 pb-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        What is risk?
                    </h2>

                    <p class="mb-4 text-slate-300">
                        Risk in information security refers to the possibility of a threat will take advantage of a
                        vulnerability of certain information and compromise an organisation.
                    </p>

                    <p class="text-slate-300">
                        According to Rhodes, risk is best managed when involving all parties who should be concerned
                        about it. It must also support the organisation's goals.
                        It is also crucial for all parties involved to have a clear risk appetite, risk acceptance
                        criteria and risk owners who can take accountability.
                    </p>
                </section>

                <section id="1" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Creating risk statements
                    </h2>

                    <p class="mb-4 text-slate-300">
                        According to Rhodes, the risk statement briefly explains the risk to stakeholders. It must
                        convey the incident
                        that is likely to happen, the consequence that will happen when security is compromised and the
                        impact it will have to the stakeholders or business.
                    </p>

                    <p class="mb-4 text-slate-300">
                        One simple format could look like this:
                    </p>

                    <p class="mb-4 text-slate-300">
                        <strong>There is a risk that [event/incident] occurs leading to [consequence] that causes
                            [impact].</strong>
                    </p>

                    <p class="mb-4 text-slate-300">
                        If-then statements can also be used to express the risk to stakeholders, risk owners and other
                        affected parties.
                    </p>

                    <p class="mb-4 text-slate-300">
                        Here are some examples:
                    </p>

                    <ul class="mb-4 list-disc space-y-3 pl-6 text-slate-300">
                        <li>If the server is infected, then an outage is likely to occur. Any outage will result in $500
                            of lost sales for every 15 minutes of downtime. </li>
                        <li>There is a risk that a staff member will click on a malicious link in an email message
                            leading to the installation of malicious software that causes the computer system to be
                            unavailable to users.</li>
                    </ul>
                </section>

                <section id="2" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Communicating risks
                    </h2>

                    <p class="mb-4 text-slate-300">
                        The stakeholders may not always be someone in IT or an information security professional, so the
                        risk must be communicated through language the stakeholders understand. Different people also
                        value different aspects of the business or the information.
                    </p>

                    <ul class="mb-4 list-disc space-y-3 pl-6 text-slate-300">
                        <li>Technology managers may care about things like system availability measured in percentages.
                        </li>
                        <li>Business managers may care about the number of transactions completed successfully per hour.
                        </li>
                        <li>Executive managers care about market share which they could measure in their own metrics.
                        </li>
                    </ul>
                </section>

                <section id="5" class="scroll-mt-24 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Sources
                    </h2>

                    <div class="space-y-3">
                        <div class="rounded-xl border border-slate-800 bg-slate-900 p-4">
                            <a class="text-cyan-400" href="https://www.iso.org/standard/73906.html">International
                                Organization for Standardization.</a> (2018).
                            ISO/IEC 27000:2018 Information technology — Security techniques —
                            Information security management systems — Overview and vocabulary.
                        </div>

                        <div class="rounded-xl border border-slate-800 bg-slate-900 p-4">
                            Rhodes, A. (2023). <em>IFN541 Information Security Management: Organisational Risk
                                Management.</em> [Presentation]. <a class="text-cyan-400"
                                href="https://www.canvas.qut.edu.au/">Canvas.</a>
                        </div>
                    </div>
                </section>

                <div class="mt-10 flex justify-between border-t border-slate-800 pt-6">
                    <NuxtLink
                        class="rounded-xl border border-slate-700 px-5 py-3 text-sm text-slate-300 hover:bg-slate-800">
                        Previous
                    </NuxtLink>

                    <InfoSecSelect /> 

                    <NuxtLink to="/courses/cybersec-intro/module2"
                        class="rounded-xl bg-cyan-500 px-5 py-3 text-sm font-semibold text-slate-950 hover:bg-cyan-400">
                        Next
                    </NuxtLink>
                </div>
            </article>

            <CourseSidebar :sections="sections" />
        </section>
    </main>
</template>