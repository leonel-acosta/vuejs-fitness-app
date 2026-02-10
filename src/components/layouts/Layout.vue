<script setup></script>

<template>
  <header>
    <h1>FITNESS APP</h1>
  </header>
  <main>
    <slot />
  </main>

  <footer>
    <small
      >created by
      <b>
        <a href="https://www.github.com/leonel-acosta" target="_blank">
          Leonel Acosta
          <img
            alt="profile"
            src="https://media.licdn.com/dms/image/v2/D4D03AQE8XDKfxn_wvA/profile-displayphoto-shrink_200_200/profile-displayphoto-shrink_200_200/0/1729173321364?e=1772064000&v=beta&t=5r3GOcN9z5Qil4cnqObNtvmUPXsI7S7yv60HHIc_nl4"
          />
          <i class="fa-brands fa-github"></i>
        </a>
      </b>
    </small>
  </footer>
</template>

<style scoped>
header,
footer,
main {
  padding: 1rem;
  width: 100%;
  max-width: 700px;
  margin: 0 auto;
}

main {
  flex: 1;
}

footer {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  align-items: center;
  padding: 3rem 0;
}

footer a {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.3rem;
  padding-right: 0.5rem;
  background: var(--background-muted);
  border: blue 1px solid transparent;
  transition-duration: 200ms;
  text-decoration: none;
}

footer a:hoover {
  border-color: var(--color-link);
}

footer a img {
  max-width: 30px;
  aspect-ratio: 1/1;
  border-radius: 100%;
}
</style>
