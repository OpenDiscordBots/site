<script lang="ts">
  const bots = ["AutoPublish", "CleanLeave", "PinRotate", "StarPin", "ThreadPersist", "ToDo"];
  let currentOffset = 0,
    currentLength = 3;
  const getVisibleBots = (offset: number, length: number) => {
    return bots.slice(offset, length + offset);
  };

  $: visibleBots = getVisibleBots(currentOffset, currentLength);

  function onShowLeft() {
    currentOffset = currentOffset - 1;
    if (currentOffset < 0) currentOffset = 0;
  }

  function onShowRight() {
    currentOffset = currentOffset + 1;
    if (currentOffset > bots.length - currentLength) currentOffset = bots.length - currentLength;
  }

  function onBotClick(bot: string) {
    window.location.href = `/bots/${bot.toLowerCase()}`;
  }
</script>

<div class="hero">
  <h3 class="header">A bot for every occasion.</h3>
  <div class="carousel">
    <button class="carouselItem action" on:click={onShowLeft} />
    {#each visibleBots as bot}
      <img
        src="{bot}.png"
        alt="{bot} Icon"
        class="carouselItem botIcon"
        on:click={() => onBotClick(bot)}
      />
    {/each}
    <button class="carouselItem action" on:click={onShowRight} />
  </div>
</div>

<style lang="scss">
  @import "src/mixins.scss";
  .hero {
    display: flex;
    flex-direction: column;
    gap: 0px;
    padding-left: 24px;
    padding-right: 24px;
  }

  .carousel {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: flex-start;
    gap: 12px;

    .carouselItem {
      width: 96px;
      height: 96px;
      border-radius: 8px;
      @include tablet {
        width: 72px;
        height: 72px;
        border-radius: 6px;
      }
      @include mobile {
        width: 48px;
        height: 48px;
        border-radius: 4px;
      }
    }

    .action {
      background-color: black;
    }
  }
</style>
