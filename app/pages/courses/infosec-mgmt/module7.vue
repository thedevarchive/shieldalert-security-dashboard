<script setup lang="ts">
useHead({
    title: 'Identity Management',
})

const sections = [
    {
        id: '0',
        title: 'Why is identity management needed?',
    },
    {
        id: '1',
        title: 'What is user authentication?',
    },
    {
        id: '2',
        title: 'Why is user authentication important?',
    },
    {
        id: '3',
        title: 'User authentication mechanisms',
    },
    {
        id: '4',
        title: 'Knowledge-based authenticators',
    },
    {
        id: '5',
        title: '',
    },
    {
        id: '6',
        title: '',
    },
    {
        id: '7',
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
                    Information Security Management: Module 7
                </p>

                <h1 class="mb-4 text-4xl font-bold">
                    Identity Management
                </h1>

                <p class="mb-8 text-slate-300">
                    Learn the concepts of identity management and the different ways users can be authenticated.
                </p>

                <div class="mb-10 rounded-2xl border border-slate-800 bg-slate-900 p-5">
                    <p class="text-sm text-slate-400">Estimated reading time</p>
                    <p class="mt-1 text-lg font-semibold">12 minutes</p>
                </div>

                <section id="0" class="scroll-mt-24 border-b border-slate-800 pb-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Why is identity management needed?
                    </h2>

                    <p class="mb-4 text-slate-300">
                        It is important for identity to be confirmed if interacting with information requires
                        verification of identity.
                        It ensures that the right people can access the right resources when they need it.
                    </p>
                </section>

                <section id="1" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        What is user authentication?
                    </h2>

                    <p class="mb-4 text-slate-300">
                        It is a process that determines if the identity user provided is authentic or not.
                        Once user provides both the identity and the credential that proves that it is them, it checks
                        what permissions the user has with the information they have access to.
                    </p>
                </section>

                <section id="2" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Why is user authentication important?
                    </h2>
                    <p class="mb-4 text-slate-300">
                        It is essential in managing information security to mitigate security incidents and unauthorised
                        users gaining access to information they are not meant to access. It is used with
                        access control and user accountability.
                        Identity management systems need to have a <strong>user identifier (ID)</strong> and <strong>a
                            way to verify the user (authenticator)</strong>.
                    </p>
                </section>

                <section id="3" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        User authentication mechanisms
                    </h2>

                    <ul class="mb-4 list-disc space-y-3 pl-6 text-slate-300">
                        <li>Knowledge-based - involves something you know (a secret you know)</li>
                        <li>Object-based - involves something you have (physical item you have)</li>
                        <li>ID-based - involves something you are (biological imprints or other physical characters)
                        </li>
                        <li>Location-based - involves where you currently are</li>
                    </ul>

                    <p class="mb-4 text-slate-300">
                        There is also multi-factor authentication that uses combinations from different categories of
                        authenticators
                    </p>
                </section>

                <section id="4" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Knowledge-based authenticators
                    </h2>

                    <p class="mb-4 text-slate-300">
                        Commonly used
                    </p>
                    <ul class="mb-4 list-disc space-y-3 pl-6 text-slate-300">
                        <li>Passwords</li>
                        <li>Personal Identification Number (PIN)</li>
                        <li>Security questions (e.g. What is your pet's name?, What is your first company?, etc)</li>
                    </ul>

                    <p class="mb-4 text-slate-300">
                        Advantages
                    </p>
                    <ul class="mb-4 list-disc space-y-3 pl-6 text-slate-300">
                        <li>Easily accepted by users</li>
                        <li>Does not cost much to implement</li>
                    </ul>
                </section>

                <section id="5" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Passwords
                    </h2>

                    <p class="mb-4 text-slate-300">
                        Reusable passwords are often used as a form of user authentication. The system stores the
                        encrypted password values while the user provides their credentials to confirm their identity.
                        The user must ensure that they must remember their password and that it is stored securely.
                    </p>

                    <p class="mb-4 text-slate-300">
                        Disadvantages
                    </p>
                    <ul class="mb-4 list-disc space-y-3 pl-6 text-slate-300">
                        <li>User may forget password</li>
                        <li>User may share or reveal password</li>
                        <li>User may compromise their password without their notice</li>
                        <li>User may use the same password when logging into to different sites</li>
                    </ul>
                </section>

                <section id="6" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                    </h2>

                    <p class="mb-4 text-slate-300">
                    </p>
                </section>

                <section id="7" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                    </h2>

                    <p class="mb-4 text-slate-300">
                    </p>
                </section>

                <section id="8" class="scroll-mt-24 border-b border-slate-800 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                    </h2>

                    <p class="mb-4 text-slate-300">
                    </p>
                </section>

                <section id="9" class="scroll-mt-24 py-10">
                    <h2 class="mb-4 text-2xl font-semibold">
                        Sources
                    </h2>

                    <div class="space-y-3">
                        <div class="rounded-xl border border-slate-800 bg-slate-900 p-4">
                            Rhodes, A. (2023). <em>IFN541 Information Security Management: Identity
                                Management.</em> [Presentation]. <a class="text-cyan-400"
                                href="https://www.canvas.qut.edu.au/">Canvas.</a>
                        </div>

                        <div class="rounded-xl border border-slate-800 bg-slate-900 p-4">
                            Rhodes, A. (2023). <em>IFN541 Information Security Management: Other User Authentication
                                Mechanisms</em> [Presentation]. <a class="text-cyan-400"
                                href="https://www.canvas.qut.edu.au/">Canvas.</a>
                        </div>
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
