<script lang="ts">
  import * as Card from "$lib/components/ui/card/index.js";
</script>

<div class="min-h-screen flex flex-col">
  <!-- Header -->
  <header class="w-full px-4 md:px-24 py-6 border-b flex items-center">
    <h1 class="text-2xl md:text-3xl font-bold">About Exima Hub</h1>
  </header>

  <!-- Main Content -->
  <main class="flex-1 px-4 md:px-24 py-10">
    <!-- Introduction Section -->
    <section class="max-w-4xl mx-auto mb-12">
      <h2 class="text-3xl md:text-4xl font-bold mb-4 text-center">Who We Are</h2>
  <p class="text-base md:text-lg leading-relaxed text-center">
        Exima Hub is dedicated to making complex information accessible and actionable. 
        We combine expertise in technology, design, and communication to deliver clear, reliable resources for everyone.
      </p>
    </section>

    <!-- Cards Grid -->
    <section class="grid grid-cols-1 md:grid-cols-2 gap-6 max-w-5xl mx-auto">
      <!-- Card 1: Our Mission -->
      <Card.Root>
        <Card.Header>
          <Card.Title>Our Mission</Card.Title>
          <Card.Description>What drives us forward</Card.Description>
        </Card.Header>
        <Card.Content>
          <p class="text-sm md:text-base leading-relaxed">
            To empower individuals and businesses with the knowledge and tools they need to succeed. 
            We believe in transparency, innovation, and putting users first in everything we do.
          </p>
        </Card.Content>
      </Card.Root>

      <!-- Card 2: Our Values -->
      <Card.Root>
        <Card.Header>
          <Card.Title>Our Values</Card.Title>
          <Card.Description>Principles that guide us</Card.Description>
        </Card.Header>
        <Card.Content>
          <ul class="list-disc list-inside text-sm md:text-base space-y-1">
            <li>Integrity and transparency</li>
            <li>Continuous improvement</li>
            <li>User-centric approach</li>
            <li>Collaboration and respect</li>
          </ul>
        </Card.Content>
      </Card.Root>

      <!-- Card 3: What We Do -->
      <Card.Root>
        <Card.Header>
          <Card.Title>What We Do</Card.Title>
          <Card.Description>Our services and solutions</Card.Description>
        </Card.Header>
        <Card.Content>
          <p class="text-sm md:text-base leading-relaxed">
            We build tools and guides that help users navigate complex topics. 
            From beginners to experts, our platform is designed to support your journey with clear documentation and intuitive interfaces.
          </p>
        </Card.Content>
      </Card.Root>

      <!-- Card 4: Our Team -->
      <Card.Root>
        <Card.Header>
          <Card.Title>Our Team</Card.Title>
          <Card.Description>The people behind Exima Hub</Card.Description>
        </Card.Header>
        <Card.Content>
          <p class="text-sm md:text-base leading-relaxed">
            Our diverse team brings together experts in software development, UX design, content creation, and business strategy. 
            We're passionate about creating meaningful experiences for our users.
          </p>
        </Card.Content>
      </Card.Root>

      <!-- Card 5: Get In Touch -->
      <Card.Root class="md:col-span-2">
        <Card.Header>
          <Card.Title>Get In Touch</Card.Title>
          <Card.Description>We'd love to hear from you</Card.Description>
        </Card.Header>
        <Card.Content>
          <div class="space-y-2 text-sm md:text-base">
            <div>
              <span class="font-semibold">Email: </span>
              <a href="mailto:info@eximahub.com" class="text-primary underline">info@eximahub.com</a>
            </div>
            <div>
              <span class="font-semibold">Address: </span>
              <span>123 Innovation Street, Istanbul, Turkey</span>
            </div>
            <div>
              <span class="font-semibold">Phone: </span>
              <span>+90 123 456 7890</span>
            </div>
          </div>
        </Card.Content>
        <Card.Footer>
          <p class="text-sm">Available Monday - Friday, 9:00 AM - 6:00 PM (GMT+3)</p>
        </Card.Footer>
      </Card.Root>
    </section>
  </main>
</div>