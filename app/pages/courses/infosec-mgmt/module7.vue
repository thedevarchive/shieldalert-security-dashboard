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
    title: 'Passwords',
  },
  {
    id: '6',
    title: 'Object-based authenticators',
  },
  {
    id: '7',
    title: 'Tokens',
  },
  {
    id: '8',
    title: 'ID-based authenticators',
  },
  {
    id: '9',
    title: 'Biometrics issues',
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
          Information Security Management: Module 7
        </p>

        <h1 class="mb-4 text-4xl font-bold">Identity Management</h1>

        <p class="mb-8 text-slate-300">
          Learn the concepts of identity management and the different ways users
          can be authenticated.
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
            It is important for identity to be confirmed if interacting with
            information requires verification of identity. It ensures that the
            right people can access the right resources when they need it.
          </p>
        </section>

        <section id="1" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
            What is user authentication?
          </h2>

          <p class="mb-4 text-slate-300">
            It is a process that determines if the identity user provided is
            authentic or not. Once user provides both the identity and the
            credential that proves that it is them, it checks what permissions
            the user has with the information they have access to.
          </p>
        </section>

        <section id="2" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
            Why is user authentication important?
          </h2>
          <p class="mb-4 text-slate-300">
            It is essential in managing information security to mitigate
            security incidents and unauthorised users gaining access to
            information they are not meant to access. It is used with access
            control and user accountability. Identity management systems need to
            have a <strong>user identifier (ID)</strong> and
            <strong>a way to verify the user (authenticator)</strong>.
          </p>
        </section>

        <section id="3" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
            User authentication mechanisms
          </h2>

          <ul class="mb-4 list-disc space-y-3 pl-6 text-slate-300">
            <li>
              Knowledge-based - involves something you know (a secret you know)
            </li>
            <li>
              Object-based - involves something you have (physical item you
              have)
            </li>
            <li>
              ID-based - involves something you are (biological imprints or
              other physical characters)
            </li>
            <li>Location-based - involves where you currently are</li>
          </ul>

          <p class="mb-4 text-slate-300">
            There is also multi-factor authentication that uses combinations
            from different categories of authenticators
          </p>
        </section>

        <section id="4" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
            Knowledge-based authenticators
          </h2>

          <p class="mb-4 text-slate-300">Commonly used</p>
          <ul class="mb-4 list-disc space-y-3 pl-6 text-slate-300">
            <li>Passwords</li>
            <li>Personal Identification Number (PIN)</li>
            <li>
              Security questions (e.g. What is your pet's name?, What is your
              first company?, etc)
            </li>
          </ul>

          <p class="mb-4 text-slate-300">Advantages</p>
          <ul class="mb-4 list-disc space-y-3 pl-6 text-slate-300">
            <li>Easily accepted by users</li>
            <li>Does not cost much to implement</li>
          </ul>
        </section>

        <section id="5" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">Passwords</h2>

          <p class="mb-4 text-slate-300">
            Reusable passwords are often used as a form of user authentication.
            The system stores the encrypted password values while the user
            provides their credentials to confirm their identity. The user must
            ensure that they must remember their password and that it is stored
            securely.
          </p>

          <p class="mb-4 text-slate-300">Disadvantages</p>
          <ul class="mb-4 list-disc space-y-3 pl-6 text-slate-300">
            <li>User may forget password</li>
            <li>User may share or reveal password</li>
            <li>User may compromise their password without their notice</li>
            <li>
              User may use the same password when logging into to different
              sites
            </li>
          </ul>
        </section>

        <section id="6" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
            Object-based authenticators
          </h2>

          <p class="mb-4 text-slate-300">
            Object-based authenticators use physical tokens to authenticate users.
          </p>

          <p class="mb-4 text-slate-300">Examples:</p>
          <ul class="mb-4 list-disc space-y-3 pl-6 text-slate-300">
            <li>Physical door key</li>
            <li>Magnetic swipe card</li>
            <li>Token used for generating access codes</li>
          </ul>

          <p class="mb-4 text-slate-300">Advantages</p>
          <ul class="mb-4 list-disc space-y-3 pl-6 text-slate-300">
            <li>Hard to share</li>
            <li>User can easily recognise if token was lost</li>
          </ul>

          <p class="mb-4 text-slate-300">Disadvantage: If lost, the person who finds it can use the token.</p>
        </section>

        <section id="7" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">Tokens</h2>

          <p class="mb-4 text-slate-300">A token could be</p>
          <ul class="mb-4 list-disc space-y-3 pl-6 text-slate-300">
            <li>A physical key</li>
            <li>A swipe card</li>
            <li>An ID badge</li>
            <li>A device that generates sequences of one-time passwords</li>
          </ul>

          <p class="mb-4 text-slate-300">
            One limitation is that it requires synchronisation. Thus, it requires a window of time that also considers
            network delays. If it is too short, it may lock out users. If it is too long, attackers could be able to
            capture the token and be able to log in.
          </p>
        </section>

        <section id="8" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
            ID-based authenticators
          </h2>

          <p class="mb-4 text-slate-300">
            ID-based authenticators refer to authenticators involving something that is unique to a person.
            These include biometrics like fingerprints, eye scans or even signatures.
            The characteristics of a biometric are that each person must have one (universality),
            no two people share the same biometric pattern (distinctiveness),
            it cannot change over time (permanence) and it should be measurable (collectability).
          </p>

          <p class="mb-4 text-slate-300">Advantages</p>
          <ul class="mb-4 list-disc space-y-3 pl-6 text-slate-300">
            <li>Cannot be forgotten or lost</li>
            <li>Difficult to copy or replicate</li>
          </ul>

          <p class="mb-4 text-slate-300">Disadvantage: It is harder to replace than passwords or tokens.</p>
        </section>

        <section id="9" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
            Biometrics issues
          </h2>

          <p class="mb-4 text-slate-300">
            Sometimes, two samples of a biometric taken from the same person would not be registered as the same because
            of imperfect imaging conditions, changes in the user's characteristics, ambient conditions or even user's
            interaction with the sensor. The captured features are also compared against the stored template and a
            difference in those samples may result in a decision error which could either reject the authorised user or
            allow an unauthorised user access.
          </p>
        </section>

        <section id="10" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
            Location-based authentication
          </h2>

          <p class="mb-4 text-slate-300">
            Location-based authentication authenticates the user based on where they are located at the current time.
            They could use tracking technologies like GPS, IP addresses or DNS names to verify the user.
          </p>

          <p class="mb-4 text-slate-300">Advantages</p>
          <ul class="mb-4 list-disc space-y-3 pl-6 text-slate-300">
            <li>Improves network security, especially when locations are local</li>
          </ul>

          <p class="mb-4 text-slate-300">Disadvantages</p>
          <ul class="mb-4 list-disc space-y-3 pl-6 text-slate-300">
            <li>Privacy issues</li>
            <li>IPs can be changed using VPNs</li>
          </ul>
        </section>

        <section id="11" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
            Multi-factor authentication
          </h2>

          <p class="mb-4 text-slate-300">
            Combining multiple authentication techniques can not only cover the weaknesses of the chosen methods, but
            also prevent attackers from gaining unauthorised access to information. Some frequently-used combinations
            are password and verification code or PIN and swipe card. 
          </p>
        </section>

        <section id="12" class="scroll-mt-24 py-10">
          <h2 class="mb-4 text-2xl font-semibold">Sources</h2>

          <div class="space-y-3">
            <div class="rounded-xl border border-slate-800 bg-slate-900 p-4">
              Rhodes, A. (2023).
              <em>IFN541 Information Security Management: Identity
                Management.</em>
              [Presentation].
              <a class="text-cyan-400" href="https://www.canvas.qut.edu.au/">Canvas.</a>
            </div>

            <div class="rounded-xl border border-slate-800 bg-slate-900 p-4">
              Rhodes, A. (2023).
              <em>IFN541 Information Security Management: Other User
                Authentication Mechanisms.</em>
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
