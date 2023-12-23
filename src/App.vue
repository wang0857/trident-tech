<script setup>
  import { reactive, ref } from 'vue';

  const navItems = reactive([
    {
      id: 'features',
      itemName: '白頭翁的特性',
      selected: true,
    },
    {
      id: 'stories',
      itemName: '白頭翁的故事',
      selected: false,
    },
    {
      id: 'photos',
      itemName: '白頭翁的美照',
      selected: false,
    },
    {
      id: 'crisis',
      itemName: '白頭翁的危機',
      selected: false,
    },
  ])

  const isExpanded = ref(false)

  function expandMenu() {
    isExpanded.value = !isExpanded.value
  }
</script>

<template>
  <div class="app-container">
    <!-- Desktop sidebar -->
    <div class="sidebar-container">
      <aside class="sidebar-nav">
        <h2>白頭翁不吃小米</h2>
        <nav class="sidebar-nav-container">
          <ul class="sidebar-nav-list">
            <li
              v-for="item in navItems"
              :id="item.id"
              class="sidebar-nav-list-item"
            >
              <a
                href="#"
                :alt="item.itemName"
                :class="item.selected ? 'sidebar-nav-list-item-link--selected' : 'sidebar-nav-list-item-link'"
              >
                {{ item.itemName }}
              </a>
            </li>
          </ul>
        </nav>
      </aside>
      <div class="logo">Logo</div>
    </div>

    <!-- Mobile Navbar -->
    <nav class="navbar-container mobile">
      <div class="navbar-bar">
        <button class="navbar-bar-menu" @click="expandMenu">
          <div class="navbar-bar-menu-bars">
            <span :class="isExpanded ? 'navbar-bar-menu-bar close' : 'navbar-bar-menu-bar'"></span>
            <span :class="isExpanded ? 'navbar-bar-menu-bar close' : 'navbar-bar-menu-bar'"></span>
            <span :class="isExpanded ? 'navbar-bar-menu-bar close' : 'navbar-bar-menu-bar'"></span>
          </div>
        </button>
        <h2>白頭翁不吃小米</h2>
        <div class="logo">Logo</div>
      </div>
      <div :class="isExpanded ? 'navbar-list-container expanded' : 'navbar-list-container'">
        <ul class="navbar-list">
          <li
            v-for="item in navItems"
            :id="item.id"
            class="navbar-list-item"
          >
            <a
              href="#"
              :alt="item.itemName"
              :class="item.selected ? 'navbar-list-item-link--selected' : 'navbar-list-item-link'"
            >
              {{ item.itemName }}
            </a>
          </li>
        </ul>
      </div>
    </nav>
    <div>
      <div>
        <header>
          <div class="header-text">
            <h1>白頭翁 (Chinese bulbul)</h1>
            <p>又名白頭鵯。以果實、昆蟲為主食，無法消化小米、穀類。平均壽命約 8~10 年。</p>
          </div>
        </header>
        <main>
          <section>
            <div>
              <div class="headerThird-container">
                <h3>外觀</h3>
                <div class="headerThird-deco"></div>
              </div>
            </div>
            <p>白頭鵯體長約17到22公分，額至頭頂純黑色而富有光澤，兩眼上方至後枕白色，形成一白色枕環。耳羽後部有一白斑，此白環與白斑在黑色的頭部均極為醒目，老鳥的枕羽(後頭部)更潔白，所以又叫「白頭翁」。</p>
          </section>
          <section>
            <div>
              <div class="headerThird-container">
                <h3>棲地</h3>
                <div class="headerThird-deco"></div>
              </div>
            </div>
            <p>白頭翁和麻雀、綠繡眼合稱「城市三寶」，常成群出現在平原區灌木叢、丘陵樹林地帶，以及校園、公園、庭院、行道中的各種高高的電線與樹上。</p>
          </section>
          <section>
            <div>
              <div class="headerThird-container">
                <h3>食性</h3>
                <div class="headerThird-deco"></div>
              </div>
            </div>
            <p>以果樹的漿果和種子為主食，並時常飛入果園偷吃果實，還會吃嫩葉嫩芽，尤其是胡蝶蘭的嫩葉嫩芽葉，偶爾啄食昆蟲。</p>
          </section>
        </main>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
  @import './scss/variables';

  .app-container {
    display: grid;
    grid-template-columns: 345px auto;
  }

  .navbar {
    &-container {
      &.mobile {
        display: none;
      }
    }
  }

  .sidebar {
    &-container {
      position: relative;
      display: block;
      background-color: $white;
      .logo {
        position: absolute;
        top: 47px;
        right: -48px;
        height: 97px;
        width: 97px;
        background-color: $white;
        border-radius: 100px;
        display: flex;
        align-items: center;
        justify-content: center;
        box-shadow: 0px 0px 6px hsla(0, 0%, 0%, 0.25);
        font-size: 18px;
      }
    }

    &-nav {
      background-color: $white;
      min-height: 100vh;
      padding: 78px 67px;

      h2 {
        font-size: 30px;
        font-weight: $bold;
      }

      &-container {
        margin-top: 75px;
      }

      &-list {
        list-style: none;
        display: flex;
        flex-direction: column;
        gap: 21px;

        &-item {
          &-link {
            text-decoration: none;
            color: $black;
            transition: $transition;

            &:hover {
              color: $deco;
            }

            &--selected {
              color: $nav-link-active;
              text-decoration: underline;
              font-weight: $bold;
            }
          }
        }
      }
    }
  }

  header {
    height: 634px;
    background-image: url('./assets/images/banner.png');
    background-size: 185%;
    background-repeat: no-repeat;
    background-position: 68% 48%;
    padding: 37px 45px;
    box-sizing: border-box;
    display: flex;
    justify-content: flex-end;
    align-items: end;
  }
  .header {
    &-text {
      color: $white;
      display: flex;
      flex-direction: column;
      align-items: end;

      h1 {
        font-size: 48px;
        font-weight: $bold;
        margin-bottom: 4px;
      }

      p {
        font-size: 18px;
      }
    }

    &Third {
      &-container {
        position: relative;

        h3 {
          font-size: 36px;
          font-weight: $bold;
        }
      }

      &-deco {
        width: 25px;
        height: 25px;
        background-image: url('./assets/images/deco.png');
        background-size: cover;
        position: absolute;
        bottom: -11px;
        right: -15px;
        z-index: 1;
      }
    }
  }

  main {
    padding: 58px 51px 84px;
    display: flex;
    gap: 79px;

    section {
      display: flex;
      gap: 37.84px;

      h3 {
        font-size: 36px;
        writing-mode: vertical-rl;
        text-orientation: upright;
      }

      p {
        font-size: 16px;
        width: 200px;
      }
    }
  }

  @media screen and (max-width: 768px) {
    .app-container {
      grid-template-columns: 1fr;
    }
    .sidebar {
      &-container {
        display: none;
      }
    }
    .navbar {
      &-container {
        &.mobile {
          display: block;
          background-color: $white;
          box-shadow: 0px 4px 4px hsla(0, 0%, 0%, 0.25);
        }
      }

      &-bar {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: $lg;

        &-menu {
          width: 24px;
          height: 18px;
          display: flex;
          justify-content: center;
          align-items: center;
          border: none;
          background-color: rgba(0, 0, 0, 0);

          &:hover {
            cursor: pointer;
          }

          &-bars {
            display: grid;
            gap: $xs;

            span {
              background-color: $black;
              height: 4px;
              transition: $transition;

              &:nth-child(2) {
                width: 15px;
              }

              &:first-child,
              &:last-child {
                width: 24px;
              }

              &:first-child.close {
                transform: rotateZ(45deg);
                margin-top: 9px;
              }

              &:nth-child(2).close {
                display: none;
              }
              
              &:last-child.close {
                transform: rotateZ(-45deg);
                margin-top: -9px;
              }
            }
          }
        }

        h2 {
          font-size: 20px;
        }

        .logo {
          width: 48px;
          height: 48px;
          display: flex;
          align-items: center;
          justify-content: center;
          border-radius: 100px;
          box-shadow: 0px 0px 6px hsla(0, 0%, 0%, 0.25);
          font-size: 18px;
        }
      }

      &-list {
        list-style: none;
        margin: 0px;
        padding: 0px;

        &-container {
          padding: 0px 124px;
          height: 0px;
          transform: scaleY(0);
          transition: $transition;

          &.expanded {
            padding: 10px 124px 45px;
            height: 100%;
            transform: scaleY(1);
            transition: $transition;
          }
        }

        &-item {
          display: flex;

          &-link {
            text-decoration: none;
            color: $black;
            padding: 9px;
            font-size: 18px;

            &--selected {
              text-decoration: underline;
              color: $nav-link-active;
              font-weight: $bold;
              padding: 9px;
              font-size: 18px;
            }
          }
        }
      }
    }

    header {
      height: 311px;
      background-size: 250%;
      background-position: 58% 48%;
      padding: 24px 23px;
    }

    .header {
      &-text {
        text-align: right;

        h1 {
          margin-bottom: 9px;
          line-height: 50px;
        }
      }
    }

    main {
      flex-direction: column;
      padding: 51px 35px 72px;
      gap: 50px;
    }
  }
</style>

<!-- TODO: Logo CSS -->
