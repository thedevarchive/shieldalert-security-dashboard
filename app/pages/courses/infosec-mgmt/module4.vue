<script setup lang="ts">
useHead({
  title: 'Security Management Frameworks and Controls Management',
})

const sections = [
  {
    id: '0',
    title: 'What are security management frameworks?',
  },
  {
    id: '1',
    title: 'ISO 27001 Information Security Management Systems',
  },
  {
    id: '2',
    title: 'ISO 27002',
  },
  {
    id: '3',
    title: 'NIST Cybersecurity Framework',
  },
  {
    id: '4',
    title: 'Cloud Security Alliance Cloud Controls Matrix',
  },
  {
    id: '5',
    title: 'What are security controls frameworks?',
  },
  {
    id: '6',
    title: 'ISO 27002',
  },
  {
    id: '7',
    title: 'Secure Controls Framework (SCF)',
  },
  {
    id: '8',
    title: 'The Center for Internet Security (CIS)',
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
        <NuxtLink
          to="/courses"
          class="mb-6 inline-block text-sm text-cyan-400 hover:text-cyan-300"
        >
          ← Back to courses
        </NuxtLink>

        <p class="mb-2 font-semibold text-cyan-400">
          Information Security Management: Module 4
        </p>

        <h1 class="mb-4 text-4xl font-bold">
          Security Management Frameworks and Controls Management
        </h1>

        <p class="mb-8 text-slate-300">
          Learn about the different security management frameworks and controls
          frameworks.
        </p>

        <div class="mb-10 rounded-2xl border border-slate-800 bg-slate-900 p-5">
          <p class="text-sm text-slate-400">Estimated reading time</p>
          <p class="mt-1 text-lg font-semibold">12 minutes</p>
        </div>

        <section id="0" class="scroll-mt-24 border-b border-slate-800 pb-10">
          <h2 class="mb-4 text-2xl font-semibold">
            What are security management frameworks?
          </h2>

          <p class="mb-4 text-slate-300">
            According to Rhodes, security management frameworks provide a
            structured management of information security for companies and
            organisations. These frameworks offer a starting point for
            organisations that do not have information management or have a
            disorganised information management. It is also used to plan
            information security in the workplace and inform stakeholders that
            risks are being managed properly.
          </p>
        </section>

        <section id="1" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
            ISO 27001 Information Security Management Systems
          </h2>

          <p class="mb-4 text-slate-300">
            According to Rhodes, this framework contains the requirements for
            implementing an Information Security Management System (ISMS). It
            aims to align risk management with the organisation's goals, so it
            works best with any organisation.
          </p>

          <p class="mb-4 text-slate-300">
            This is a framework often used in countries like the UK and
            Australia, but is less popular in the United States. In fact, most
            Queensland State Government agencies are required to have an ISMS
            based on the framework stated in ISO 27001.
          </p>
        </section>

        <section id="2" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">ISO 27002</h2>

          <p class="mb-4 text-slate-300">
            This is a popular framework that also pairs well with ISO 27001. It
            is also known for covering controls that are not necessarily
            technology-based.
          </p>

          <p class="mb-4 text-slate-300">
            However, both ISO 27001 and 27002 costs money to own. Moreover, ISO
            27002 requires an information security professional to apply it
            since implementation of the controls are difficult to understand. It
            also does not provide mappings to other well-known frameworks.
          </p>
        </section>

        <section id="3" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
            NIST Cybersecurity Framework
          </h2>

          <p class="mb-4 text-slate-300">
            While this framework was made by the US Government, it can be used
            by any sector from any industry. This framework also focuses on the
            big picture of cybersecurity. The NIST documents are available
            without cost and has been frequently reviewed and updated by the US
            government and industry professionals. It also comes with special
            publications to allow the organisation to customise their own
            information security program.
          </p>
        </section>

        <section id="4" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
            Cloud Security Alliance Cloud Controls Matrix
          </h2>

          <p class="mb-4 text-slate-300">
            The Cloud Security Alliance (CSA) Cloud Controls Matrix is a
            controls management framework for cloud service providers. However,
            it is not suited for other organisations. While it is not an
            information security management framework, it does supply
            third-party risk management.
          </p>
        </section>

        <section id="5" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
            What are security controls frameworks?
          </h2>

          <p class="mb-4 text-slate-300">
            Security controls frameworks have a baseline standard to measure the
            maturity of implemented controls. They are an ideal choice for
            professionals who are not experts in information security,
            especially when the current controls implemented are disorganised or
            minimal. They also ensure that all possible controls are regarded
            while planning and performing risk assessments.
          </p>
        </section>

        <section id="6" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">ISO 27002</h2>

          <p class="mb-4 text-slate-300">
            ISO 27002 not only supplements the security framework ISO 27001, it
            also has a list of controls for implementing an information security
            management system. It also has controls for managing risk.
          </p>
        </section>

        <section id="7" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
            Secure Controls Framework (SCF)
          </h2>

          <p class="mb-4 text-slate-300">
            The SCF is a list of about 750 catalogued controls that allows
            businesses to create and maintain secure processes and systems.
            Designed by information security and privacy professionals, it
            provides controls suitable for both cybersecurity and privacy, and
            covers 32 domains such as asset management, cloud security and more.
            The controls listed also may not involve technology.
          </p>

          <p class="mb-4 text-slate-300">
            Moreover, it is free to view and implement and can be customised to
            the business's needs. It also contains questions for performing a
            maturity assessment. However, this framework requires an information
            security professional to apply the controls.
          </p>
        </section>

        <section id="8" class="scroll-mt-24 border-b border-slate-800 py-10">
          <h2 class="mb-4 text-2xl font-semibold">
            The Center for Internet Security (CIS)
          </h2>

          <p class="mb-4 text-slate-300">
            Contains practical resources such as
          </p>

          <ul class="mb-4 list-disc space-y-3 pl-6 text-slate-300">
            <li>CIS Controls</li>
            <li>CIS Benchmarks</li>
            <li>CIS Hardened Images</li>
          </ul>

          <p class="mb-4 text-slate-300">
            The CIS Controls are a list of 20 controls that should be
            prioritised, and are based on the best defences against common
            attacks. However, it is best used when it is customised to the
            business's priorities and which assets require the most security.
            CIS also has a free risk assessment in CIS Risk Assessment Method
            (CIS RAM) to allow users to knows which controls to prioritise. The
            CIS Controls is not only free, but it also has many accessible
            educational resources for implementing them. However, it only has
            technology controls and not a lot of information on how to map it to
            other controls frameworks.
          </p>

          <p class="mb-4 text-slate-300">
            The benchmarks were created as a configuration guide for many
            devices, software and operating systems. The hardended images
            referred to versions of an operating system were unused features are
            disabled. These are available for deployment in AWS, Google Cloud,
            Azure and Oracle Cloud.
          </p>
        </section>

        <section id="9" class="scroll-mt-24 py-10">
          <h2 class="mb-4 text-2xl font-semibold">Sources</h2>

          <div class="space-y-3">
            <div class="rounded-xl border border-slate-800 bg-slate-900 p-4">
              Rhodes, A. (2023).
              <em
                >IFN541 Information Security Management: Security Management
                Frameworks.</em
              >
              [Presentation].
              <a class="text-cyan-400" href="https://www.canvas.qut.edu.au/"
                >Canvas.</a
              >
            </div>
          </div>
        </section>

        <div class="mt-10 flex justify-between border-t border-slate-800 pt-6">
          <NuxtLink
            to="/courses/infosec-mgmt/module3"
            class="rounded-xl border border-slate-700 px-5 py-3 text-sm text-slate-300 hover:bg-slate-800"
          >
            Previous
          </NuxtLink>

          <SelectInfoSec />

          <NuxtLink
            to="/courses/infosec-mgmt/module5"
            class="rounded-xl bg-cyan-500 px-5 py-3 text-sm font-semibold text-slate-950 hover:bg-cyan-400"
          >
            Next
          </NuxtLink>
        </div>
      </article>

      <CoursesSidebar :sections="sections" />
    </section>
  </main>
</template>
