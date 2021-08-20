<template>
  <div class="footer">
    <p class="footer__text">
      TERMENI SI CONDITII: ACESTA ESTE UN SERVICIU DE DIVERTISMENT. PRIN
      FOLOSIREA LUI DECLARATI CA AVETI 18 ANI IMPLINITI,
    </p>
  </div>
</template>

<script>
export default {};
</script>

<style>
.footer {
  margin-top: 0.3rem;
  padding: 0 0.65rem;
  max-width: 480px;
}

.footer__text {
  font-size: 0.35rem;
  text-align: center;
  text-transform: uppercase;
  letter-spacing: 0.15rem;
  line-height: 0.5rem;
  max-height: 1rem;
  color: #9d9d9d;
  text-overflow: clip;
}

@media (min-width: 1440px) {
  .footer__text {
    font-size: 0.6rem;
    line-height: 0.9rem;
    max-height: 1.8rem;
  }
}
</style>