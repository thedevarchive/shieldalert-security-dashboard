<script setup lang="ts">
useHead({
  title: 'Cryptography',
})

const sections = [
  {
    id: '0',
    title: 'What is cryptography?',
  },
  {
    id: '1',
    title: 'Cryptographic terminology',
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
    id: '6',
    title: '',
  },
  {
    id: '7',
    title: '',
  },
  {
    id: '8',
    title: '',
  },
  {
    id: '9',
    title: '',
  },
  {
    id: '10',
    title: '',
  },
  {
    id: '11',
    title: '',
  },
  {
    id: '12',
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
          Information Security Management: Module 8
        </p>

        <h1 class="mb-4 text-4xl font-bold">Cryptography</h1>

        <p class="mb-8 text-slate-300">
          Learn about cryptography and how it is used to protect digital information.
        </p>

        <div class="mb-10 rounded-2xl border border-slate-800 bg-slate-900 p-5">
          <p class="text-sm text-slate-400">Estimated reading time</p>
          <p class="mt-1 text-lg font-semibold">12 minutes</p>
        </div>

        <section id="0" class="scroll-mt-24 border-b border-slate-800 pb-10">
          <h2 class="mb-4 text-2xl font-semibold">
            What is cryptography?
          </h2>

          <p class="mb-4 text-slate-300">
            Cryptography is the study of ways to keep a body of writing a secret. It is also the study of how a secret
            writing can be uncovered. It uses an algorithm, or a set of instructions, and some secret knowledge to produce the secret writing.
          </p>
        </section>

        <section id="1" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
            Cryptographic terminology
          </h2>

          <p class="mb-4 text-slate-300">
          </p>
        </section>

        <section id="2" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
          </h2>
          <p class="mb-4 text-slate-300">
          </p>
        </section>

        <section id="3" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
          </h2>

          <p class="mb-4 text-slate-300">
          </p>
        </section>

        <section id="4" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
          </h2>

          <p class="mb-4 text-slate-300"></p>
        </section>

        <section id="5" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold"></h2>

          <p class="mb-4 text-slate-300">
          </p>
        </section>

        <section id="6" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
          </h2>

          <p class="mb-4 text-slate-300">
          </p>
        </section>

        <section id="7" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold"></h2>

          <p class="mb-4 text-slate-300">
          </p>
        </section>

        <section id="8" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
          </h2>

          <p class="mb-4 text-slate-300">
          </p>
        </section>

        <section id="9" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
          </h2>

          <p class="mb-4 text-slate-300">
          </p>
        </section>

        <section id="10" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
          </h2>

          <p class="mb-4 text-slate-300">
          </p>
        </section>

        <section id="11" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
          </h2>

          <p class="mb-4 text-slate-300">
          </p>
        </section>

        <section id="12" class="scroll-mt-24 py-10">
          <h2 class="mb-4 text-2xl font-semibold">Sources</h2>

          <div class="space-y-3">
            <div class="rounded-xl border border-slate-800 bg-slate-900 p-4">
              Rhodes, A. (2023).
              <em>IFN541 Information Security Management: Cryptography. Part A: What is cryptography?</em>
              [Presentation].
              <a class="text-cyan-400" href="https://www.canvas.qut.edu.au/">Canvas.</a>
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
