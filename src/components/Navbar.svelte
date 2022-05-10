<script>
  function onLogoClick() {
    window.location.href = "/";
  }
</script>

<div role="navigation" class="navigationContainer">
  <div class="logoContainer" on:click={onLogoClick}>
    <img src="OpenDiscordBots.png" alt="Logo" class="logo" />
    <span class="name">OpenDiscordBots</span>
  </div>
  <div class="navLinkContainer">
    <a href="/github" class="navLink">GitHub</a>
    <a href="/support" class="navLink">Support</a>
  </div>
</div>

<style lang="scss">
  @import "../mixins.scss";

  .navigationContainer {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    padding-left: 24px;
    padding-right: 24px;
    padding-top: 12px;
    padding-bottom: 12px;
    gap: 12px;
    @include mobile {
      align-items: flex-start;
      flex-direction: column;
      gap: 0px;
    }
  }

  .logoContainer {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: flex-start;
    cursor: pointer;
    padding-top: 4px;
    padding-bottom: 4px;
    height: 48px;
    gap: 12px;
    .name {
      font-weight: 700;
      color: black;
    }
    &:hover {
      .name {
        text-decoration: underline;
      }
    }
  }

  .navLinkContainer {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: flex-end;
    gap: 12px;
    @include mobile {
      gap: 24px;
    }
    .navLink {
      display: flex;
      align-items: center;
      color: black;
      height: 48px;
    }
  }

  .logo {
    width: 32px;
    height: 32px;
    border-radius: 4px;
  }
</style>
