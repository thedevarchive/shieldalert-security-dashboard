<script setup lang="ts">
import InfoSecSelect from '~/components/selects/InfoSecSelect.vue';

const sections = [
    {
        id: '0',
        title: 'What are security management frameworks?',
    },
    {
        id: '1',
        title: 'Examples of security management frameworks',
    },
    {
        id: '2',
        title: 'ISO 27001 Information Security Management Systems',
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
                    Information Security Management: Module 3
                </p>

                <h1 class="mb-4 text-4xl font-bold">
                    Security Management Frameworks
                </h1>

                <p class="mb-8 text-slate-300">
                    Learn about the different security management frameworks.
                </p>

                <div class="mb-10 rounded-2xl border border-slate-800 bg-slate-900 p-5">
                    <p class="text-sm text-slate-400">Estimated reading time</p>
                    <p class="mt-1 text-lg font-semibold">5 minutes</p>
                </div>

                <section id="0" class="scroll-mt-24 border-b border-slate-800 pb-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        What are security management frameworks?
                    </h2>

                    <p class="mb-4 text-slate-300">
                        According to Rhodes, security management frameworks provide a structured management of
                        information security for companies and organisations.
                        These frameworks offer a starting point for organisations that do not have information
                        management or have a disorganised information management.
                        It is also used to plan information security in the workplace and inform stakeholders that risks
                        are being managed properly.
                    </p>
                </section>

                <section id="1" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Examples of security management frameworks
                    </h2>

                    <p class="mb-4 text-slate-300">
                    </p>
                </section>

                <section id="2" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        ISO 27001 Information Security Management Systems
                    </h2>

                    <p class="mb-4 text-slate-300">
                        According to Rhodes, this framework contains the requirements for implementing an Information
                        Security Management System (ISMS). It aims to align risk management with the organisation's goals, so it works best with any organisation. 
                    </p>

                    <p class="mb-4 text-slate-300">
                        This is a framework often used in countries like the UK and Australia, but is less popular in
                        the United States.
                        In fact, most Queensland State Government agencies are required to have an ISMS based on the
                        framework stated in ISO 27001.
                    </p>
                </section>

                <section id="3" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        ISO 27002
                    </h2>

                    <p class="mb-4 text-slate-300">
                        This is a popular framework that also pairs well with ISO 27001. 
                        It is also known for covering controls that are not necessarily technology-based. 
                    </p>

                    <p class="mb-4 text-slate-300">
                        However, both ISO 27001 and 27002 costs money to own. 
                        Moreover, ISO 27002 requires an information security professional to apply it since implementation of the controls are difficult to understand.
                        It also does not provide mappings to other well-known frameworks. 
                    </p>
                </section>

                <section id="4" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        NIST Cybersecurity Framework
                    </h2>

                    <p class="mb-4 text-slate-300">
                        While this framework was made by the US Government, it can be used by any sector from any industry. 
                        This framework also focuses on the big picture. 
                    </p>

                    <p class="mb-4 text-slate-300">
                    </p>
                </section>

                <section id="5" class="scroll-mt-24 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Sources
                    </h2>

                    <div class="space-y-3">
                        <div class="rounded-xl border border-slate-800 bg-slate-900 p-4">
                            Rhodes, A. (2023). <em>IFN541 Information Security Management: Security Management
                                Frameworks.</em> [Presentation]. <a class="text-cyan-400"
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