<script>
  let saidYes = $state(false);
  let noButtonPosition = $state({ x: 0, y: 0 });
  let noLabelIndex = $state(0);

  const noButtonMessages = [
    'No',
    'Try again 😊',
    'Pretty please?',
    'Maybe later?',
    'Sure?',
    'Yes, but disguised',
    'Nope 👀',
    'Try again 💕',
    'Not that one!',
    'The other button!',
    'Pleeease?',
    'Wrong one!',
    'Try again 💖',
    'So close!',
    'One more try?',
    /* German */
    'Bitte bitte?',
    'Probier nochmal 😊',
    'Der andere Knopf!',
    'Nee, oder?',
    'Bitte sag Ja! 💕',
    /* Russian */
    'Попробуй ещё раз!',
    'Не та кнопка!',
    'Ну пожалуйста!',
    'Другая кнопка!',
    'Скажи да! 💖',
    /* Swedish */
    'Försök igen!',
    'Snälla?',
    'Fel knapp!',
    'Den andra knappen!',
    'Säg ja! 😊',
  ];

  function shuffle(arr) {
    const a = [...arr];
    for (let i = a.length - 1; i > 0; i--) {
      const j = Math.floor(Math.random() * (i + 1));
      [a[i], a[j]] = [a[j], a[i]];
    }
    return a;
  }

  const noButtonMessagesOrder = ['No', ...shuffle(noButtonMessages.slice(1))];

  function handleNoClick() {
    const offset = 24 + Math.random() * 24;
    const angle = Math.random() * Math.PI * 2;
    /* Keep No button inside canvas: don't overlap Yes, image, text, or escape frame */
    const xMin = -52;
    const xMax = 72;
    const yMin = 0;
    const yMax = 58;
    noButtonPosition = {
      x: Math.max(xMin, Math.min(xMax, noButtonPosition.x + Math.cos(angle) * offset)),
      y: Math.max(yMin, Math.min(yMax, noButtonPosition.y + Math.sin(angle) * offset)),
    };
    noLabelIndex = (noLabelIndex + 1) % noButtonMessagesOrder.length;
  }

  function handleYesClick() {
    saidYes = true;
  }
</script>

<main class="valentine">
  <div class="frame">
    {#if saidYes}
      <div class="success">
        <h1>💖 Yayy my silly goose 💖</h1>
        <img src="/img/celebrate.gif" alt="Celebration" class="gif success-gif" />
      </div>
    {:else}
      <h1>Michelle, will you be my Valentine?</h1>
      <img src="/img/please.gif" alt="Two cute bears" class="gif" />
      <div class="buttons">
        <button type="button" class="btn btn-yes" onclick={handleYesClick}>
          Yes
        </button>
        <button
          type="button"
          class="btn btn-no"
          onclick={handleNoClick}
          style="transform: translate({noButtonPosition.x}px, {noButtonPosition.y}px)"
        >
          {noButtonMessagesOrder[noLabelIndex]}
        </button>
      </div>
    {/if}
  </div>
</main>
