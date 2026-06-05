<script setup lang="ts">
const sections = [
  {
    id: '0',
    title: 'What is information security?',
  },
  {
    id: '1',
    title: 'Common warning signs',
  },
  {
    id: '2',
    title: 'Security goals',
  },
  {
    id: '3',
    title: 'Additional security goals',
  },
  {
    id: '4',
    title: 'Security controls',
  },
  {
    id: '5',
    title: 'Sources',
  },
]

const selectedModule = ref('')

const modules = [
  {
    title: 'Information Security Fundamentals',
    path: '/courses/infosec-mgmt/module1',
  },
  {
    title: 'Risk Statements',
    path: '/courses/infosec-mgmt/module2',
  },
]

function goToModule() {
  if (selectedModule.value) {
    navigateTo(selectedModule.value)
  }
}
</script>

<template>
  <main class="min-h-screen bg-slate-950 text-white">
    <section class="mx-auto flex max-w-7xl gap-8 px-6 py-10">
      <article class="max-w-3xl flex-1">
        <NuxtLink to="/courses" class="mb-6 inline-block text-sm text-cyan-400 hover:text-cyan-300">
          ← Back to courses
        </NuxtLink>

        <p class="mb-2 font-semibold text-cyan-400">
          Information Security Management: Module 1
        </p>

        <h1 class="mb-4 text-4xl font-bold">
          Information Security Fundamentals
        </h1>

        <p class="mb-8 text-slate-300">
          Learn why information security management means and why it is needed by industries and organisations.
        </p>

        <div class="mb-10 rounded-2xl border border-slate-800 bg-slate-900 p-5">
          <p class="text-sm text-slate-400">Estimated reading time</p>
          <p class="mt-1 text-lg font-semibold">8 minutes</p>
        </div>

        <section id="0" class="scroll-mt-24 border-b border-slate-800 pb-10">
          <h2 class="mb-4 text-2xl font-semibold">
            What is information security?
          </h2>

          <p class="mb-4 text-slate-300">
            Information security focuses on the protection of information and the technology that stores or transfers
            them.
          </p>

          <p class="text-slate-300">
            Information security is essential because information has certain characteristics that provide value, and if
            one of them is violated, the information is no longer useful.
            The three characteristics that make information valuable are <strong>confidentiality, integrity and
              availability.</strong>
          </p>
        </section>

        <section id="1" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
            Why is information security management needed?
          </h2>

          <p class="mb-4 text-slate-300">
            Nowadays, there are many problems involving information security.
          </p>

          <p class="mb-4 text-slate-300">
            One such example is the collapse of the Australian hedge fund Levitas Capital.
            According to the ACS Information Age article, the scam started with a spoofed Zoom
            invitation.
            After accessing the link, a hedge fund manager unknowingly installed malware and lost access to his email
            account.
            Then, attackers transferred about $8.7 million to several different accounts.
            While the hedge fund manager was able to stop the transfers, it was too late.
            After the cyberattack, Levitas Capital is no longer in operation.
          </p>

          <p class="mb-4 text-slate-300">
            Another example is the cyberattack that happened to Queensland University of Technology (QUT) in late 2022.
            One day, attackers targeted the university's internal storage drive, exposing current and former staff and
            student's personal details.
            The attack also involved the campus printers printing out ransomware notes several times,
            which asked for a "modest royalty" to keep the data under wraps (Darwen, 2024).
          </p>

          <p class="mb-4 text-slate-300">
            A more recent example is the Canvas breach that happened during May 2026.
            Canvas is a Learning Management System (LMS) managed by Instructure.
            On May 1, Steve Proud, the Chief Information Security Officer of Instructure, said that Canvas
            "recently experienced a cybersecurity incident perpetrated by a criminal threat actor."
            On May 6, he said that the company finished their investigation and did not find any suspicious activity.
          </p>

          <p class="mb-4 text-slate-300">
            However, according to a ZDNet article that reported the incident, students later discovered
            login issues.
            One day later, Canvas' login interface was vandalised with ransom notes posted by the instigators of the
            ongoing attack, asking Instructure to contact the attacker group.
            The group also stole personal information from about 275 million students from roughly 9,000 schools from
            all around the world.
            While access to the site is restored, this has left a devastating impact on Instructure's reputation.
          </p>

          <p class="mb-4 text-slate-300">
            Based on these incidents, usage of ransomware to threaten victims is the new normal.
            These cyberattacks could happen to any company in any industry, which is why information security is more
            necessary that it was before.
          </p>
        </section>

        <section id="2" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
            Security goals
          </h2>

          <p class="mb-4 text-slate-300">
            According to Rhodes, the traditional definition of information security includes three fundamental
            goals.
          </p>

          <p class="mb-4 text-slate-300">
            These are
          </p>

          <ul class="mb-4 list-disc space-y-3 pl-6 text-slate-300">
            <li>Confidentiality,</li>
            <li>Integrity, and</li>
            <li>Availability.</li>
          </ul>

          <p class="mb-4 text-slate-300">These three can be remembered by the abbreviation "CIA".</p>

          <p class="mb-4 text-slate-300">
            Confidentiality refers to the limiting of access to the information to only those who need or use it, and
            preventing access to those who do not.
            Integrity refers to the completeness and wholeness of data. When data is altered, corrupted or damaged
            during entry, storage or transmission, it loses its integrity.
            Availability describes how accessible data is to those who need it. The data must also be in readable
            format.
          </p>

          <p class="mb-4 text-slate-300">
            Note that confidentiality and privacy are different terms. Privacy is the end goal of information security
            while confidentiality is the means to attain security.
          </p>
        </section>

        <section id="3" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
            Additional security goals
          </h2>

          <p class="mb-4 text-slate-300">
            According to Rhodes, these additional goals could also be considered necessary to establish security.
          </p>

          <ul class="mb-4 list-disc space-y-3 pl-6 text-slate-300">
            <li>Identification</li>
            <li>Authentication</li>
            <li>Authorisation</li>
            <li>Accountability</li>
            <li>Non-repudiation</li>
          </ul>

          <p class="mb-4 text-slate-300">
            Identification refers to the system's ability to recognise users and who has rightful access to the
            information.
            Authentication verifies the user's identity.
            Authorisation specifies what the user is allowed to do with the data.
            Accountability is when a system or control keeps track of activity done to the data. Each activity should
            also be traced back to the person who did the activity.
            Non-repudiation refers to creating irrefutable proof that the activity occurred and the user has done it.
          </p>
        </section>

        <section id="4" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
            Security controls
          </h2>

          <p class="mb-4 text-slate-300">
            According to Rhodes, controls refer to the measures taken to counter security threats, reduce
            vulnerabilities or prevent attacks.
          </p>

          <p class="mb-4 text-slate-300">
            There are three kinds of controls:
          </p>

          <ul class="mb-4 list-disc space-y-3 pl-6 text-slate-300">
            <li>Preventive</li>
            <li>Detective</li>
            <li>Corrective</li>
          </ul>

          <p class="mb-4 text-slate-300">
            Preventive controls reduce the occurrence of incidents, detective controls identify incidents or incoming
            attacks, while corrective controls correct or restore the data or files that were corrupted during an attack
            or incident.
          </p>
        </section>

        <section id="5" class="scroll-mt-24 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
            Sources
          </h2>

          <div class="space-y-3">
            <div class="rounded-xl border border-slate-800 bg-slate-900 p-4">
              Tonkin, C. (2020). <em>Dodgy Zoom invite brings down $75m hedge fund. </em>
              <a class="text-cyan-400"
                href="https://ia.acs.org.au/article/2020/dodgy-zoom-invite-brings-down--75m-hedge-fund.html">ACS
                Information Age.</a>
            </div>

            <div class="rounded-xl border border-slate-800 bg-slate-900 p-4">
              Tassell, D. (2022). <em>Queensland University of Technology dealing with cybersecurity attack. </em>
              <a class="text-cyan-400"
                href="https://7news.com.au/news/cyber-security/queensland-university-of-technology-dealing-with-cybersecurity-attack-leaving-students-data-exposed-c-9247260">7NEWS.</a>
            </div>

            <div class="rounded-xl border border-slate-800 bg-slate-900 p-4">
              Osborne, C. (2026). <em>Worried about the nationwide Canvas data breach? Take these 6 steps now. </em>
              <a class="text-cyan-400" href="https://status.instructure.com/incidents/9wm4knj2r64z">Instructure.</a>
            </div>

            <div class="rounded-xl border border-slate-800 bg-slate-900 p-4">
              Proud, S. (2026). <em>Confirmed Security Incident. </em>
              <a class="text-cyan-400"
                href="https://www.zdnet.com/article/canvas-breach-disrupts-schools-nationwide-6-steps-to-take-now/">ZDNet.</a>
            </div>

            <div class="rounded-xl border border-slate-800 bg-slate-900 p-4">
              Rhodes, A. (2023). <em>IFN541 Information Security Management: Why we need Information Security
                Management.</em> [Presentation]. <a class="text-cyan-400"
                href="https://www.canvas.qut.edu.au/">Canvas.</a>
            </div>

            <div class="rounded-xl border border-slate-800 bg-slate-900 p-4">
              Rhodes, A. (2023). <em>IFN541 Information Security Management: Fundamental Information Security
                Concepts.</em> [Presentation]. <a class="text-cyan-400"
                href="https://www.canvas.qut.edu.au/">Canvas.</a>
            </div>
          </div>
        </section>

        <div class="mt-10 flex justify-between border-t border-slate-800 pt-6">
          <NuxtLink class="rounded-xl border border-slate-700 px-5 py-3 text-sm text-slate-300 hover:bg-slate-800">
            Previous
          </NuxtLink>

          <div>
            <select v-model="selectedModule" @change="goToModule"
              class="rounded-lg border border-slate-700 bg-slate-900 px-3 py-2 text-white">
              <option value="">Jump to module…</option>
              <option v-for="module in modules" :key="module.title" :value="module.path">{{ module.title }}</option>
            </select>
          </div>

          <NuxtLink to="/courses/infosec-mgmt/module2"
            class="rounded-xl bg-cyan-500 px-5 py-3 text-sm font-semibold text-slate-950 hover:bg-cyan-400">
            Next
          </NuxtLink>
        </div>
      </article>

      <CourseSidebar :sections="sections" />
    </section>
  </main>
</template>