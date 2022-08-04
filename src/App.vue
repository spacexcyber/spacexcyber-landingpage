<script setup>
import { ref, getCurrentInstance, onMounted } from "vue";

const activeIndex = ref("1");
const { proxy } = getCurrentInstance();
const handleSelect = (key, keyPath) => {
  console.log(key, keyPath);
};
let activeMenu = ref("home");
const scrollTo = (name) => {
  const component = proxy.$el.querySelector(`#${activeMenu.value}`);
  if (component) {
    window.scrollTo(0, component.offsetTop);
  }
};
const menuClick = (name) => {
  activeMenu.value = name;
  scrollTo();
};
onMounted(() => {
  scrollTo();
});
</script>

<template>
  <div class="bg landing-page">
    <nav class="navbar navbar-expand-lg text-uppercase fixed-top" id="mainNav">
      <div class="container">
        <a class="navbar-brand logo" @click="menuClick('home')"></a>
        <button
          class="
            navbar-toggler
            text-uppercase
            font-weight-bold
            text-white
            rounded
          "
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarResponsive"
          aria-controls="navbarResponsive"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          Menu
          <i class="fas fa-bars"></i>
        </button>
        <div class="collapse navbar-collapse" id="navbarResponsive">
          <ul class="navbar-nav">
            <li class="nav-item mx-0 mx-lg-1">
              <a
                class="nav-link py-3 px-0 px-lg-3"
                :class="activeMenu === 'home' ? 'active' : ''"
                @click="menuClick('home')"
                >Home</a
              >
            </li>
            <li class="nav-item mx-0 mx-lg-1">
              <a
                class="nav-link py-3 px-0 px-lg-3"
                :class="activeMenu === 'spaceship' ? 'active' : ''"
                @click="menuClick('spaceship')"
                >spaceship</a
              >
            </li>
            <li class="nav-item mx-0 mx-lg-1">
              <a
                class="nav-link py-3 px-0 px-lg-3"
                :class="activeMenu === 'roadmap' ? 'active' : ''"
                @click="menuClick('roadmap')"
                >roadmap</a
              >
            </li>
            <li class="nav-item mx-0 mx-lg-1">
              <a
                class="nav-link py-3 px-0 px-lg-3"
                :class="activeMenu === 'tokenomics' ? 'active' : ''"
                @click="menuClick('tokenomics')"
                >TOKENNOMICS</a
              >
            </li>
            <li class="nav-item mx-0 mx-lg-1">
              <a
                class="nav-link py-3 px-0 px-lg-3"
                href="https://whitepaper.spacexcyber.io"
                target="_blank"
                >Whitepaper</a
              >
            </li>
            <li class="nav-item mx-0 mx-lg-1">
              <a class="nav-link py-3 px-0 px-lg-3">marketplace</a>
            </li>
          </ul>
        </div>
      </div>
    </nav>
    <div class="section-container">
      <!-- Masthead-->
      <section
        class="
          page-section
          masthead
          text-white text-center
          d-flex
          align-items-center
          vh-100
        "
        id="home"
      >
        <div class="container d-flex align-items-center flex-column">
          <!-- Masthead Heading-->
          <h1 class="masthead-heading text-uppercase mb-0">
            METAVERSE UNIVERSE
          </h1>
          <h1 class="masthead-heading text-uppercase mb-0">THE #1 SPACE MMO</h1>
          <p class="masthead-subheading font-weight-light mb-0 mt-3">
            <a class="btn btn-xl btn-win" href="#"> </a>
            <a class="btn btn-xl btn-apk" href="#"> </a>
            <a class="btn btn-xl btn-mac" href="#"> </a>
          </p>
          <div class="row mt-5">
            <div class="col">
              <div class="lead" style="width: 83rem">
                <div>
                  SpaceX Cyber is a special universe inspired by the theory of
                  multiple universes where many parallel universes coexist.
                </div>
                <div>
                  In the SpaceX Cyber ​​world, the earth is invaded by another
                  parallel universe civilization, here, after a long time of
                  war, people have absorbed and developed advanced science and
                  technology.... Now, The Earth enters the space age.
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
      <!-- Spaceship Section-->
      <section class="page-section vh-100" id="spaceship">
        <div class="container text-white">
          <div class="title">
            <span class="title-border"></span
            ><span class="title-content"
              >What is Space<span style="color: #ff6600">X</span>Cyber</span
            >
          </div>
          <div class="row mt-5 page-section-content">
            <div class="col">
              <p class="lead">
                SpaceX Cyber is an MMORPG built on blockchain, where players
                control spaceships to explore, fight and win rewards.
              </p>
              <p class="lead">
                Experience space exploration, massive PvP and PvE battles, and a
                thriving player economy in an ever-expanding sandbox.
              </p>
              <p class="lead">
                Take part in many professions and activities in the game,
                including war, piracy, trade and exploration, with hundreds of
                thousands of other players.
              </p>
            </div>
          </div>
        </div>
      </section>
      <!-- spaceship Section-->
      <section class="page-section vh-100">
        <div class="container text-white">
          <div class="title">
            <span class="title-border"></span
            ><span class="title-content">SPACESHIP OVERVIEW</span>
          </div>
          <div class="row mt-1 page-section-content">
            <div class="col">
              <p class="lead">A SMALL SAMPLE OF THE 1000+ NFT YOU CAN FLY</p>
            </div>
          </div>
        </div>
      </section>
      <!-- roadmap Section-->
      <section class="page-section vh-100" id="roadmap">
        <div class="container text-white">
          <div class="title">
            <span class="title-border"></span
            ><span class="title-content">ROADMAP</span>
          </div>
          <div class="row mt-5 page-section-content">
            <div class="col">
              <p class="lead">
                SpaceX Cyber is an MMORPG built on blockchain, where players
                control spaceships to explore, fight and win rewards.
              </p>
              <p class="lead">
                Experience space exploration, massive PvP and PvE battles, and a
                thriving player economy in an ever-expanding sandbox.
              </p>
              <p class="lead">
                Take part in many professions and activities in the game,
                including war, piracy, trade and exploration, with hundreds of
                thousands of other players.
              </p>
            </div>
          </div>
        </div>
      </section>
      <!-- Token Section-->
      <section class="page-section vh-100" id="tokenomics">
        <div class="container text-white">
          <div class="title">
            <span class="title-border"></span
            ><span class="title-content">TOKENNOMICS</span>
          </div>
          <div class="mt-5 bg-tokenomic"></div>
        </div>
      </section>
      <!-- Partner Section-->
      <section class="page-section vh-100" id="partner">
        <div class="container text-white">
          <div class="title">
            <span class="title-border"></span
            ><span class="title-content">Partner and backer</span>
          </div>
          <div class="row mt-5 page-section-content">
            <div class="col">
              <p class="lead">
                SpaceX Cyber is an MMORPG built on blockchain, where players
                control spaceships to explore, fight and win rewards.
              </p>
              <p class="lead">
                Experience space exploration, massive PvP and PvE battles, and a
                thriving player economy in an ever-expanding sandbox.
              </p>
              <p class="lead">
                Take part in many professions and activities in the game,
                including war, piracy, trade and exploration, with hundreds of
                thousands of other players.
              </p>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<style scoped>
.landing-page.bg {
  background: url("./assets/images/bg-full.jpg") no-repeat;
  height: 100%;
  background-size: cover;
}

.landing-page .logo {
  background: url("./assets/images/sp-logo.svg") no-repeat;
  width: 148px;
  height: 76px;
}

.landing-page .title {
  text-transform: uppercase;
  color: #fff;
}
.landing-page .title .title-border {
  border-left: 5px solid #ff6600;
  padding-left: 1.5rem;
  height: 32px;
  display: inline-block;
}
.landing-page .title .title-content {
  font-size: 45px;
}
.landing-page .page-section-content {
  width: 42rem;
}
.landing-page .bg-tokenomic {
  background: url("./assets/images/tokenomic.png") no-repeat;
  height: 598px;
}
.btn-win {
  background: url("./assets/images/btn-win.png") no-repeat;
  background-size: 100% 100%;
  width: 156px;
  height: 52px;
}

.btn-apk {
  background: url("./assets/images/btn-apk.png") no-repeat;
  background-size: 100% 100%;
  width: 156px;
  height: 52px;
}

.btn-mac {
  background: url("./assets/images/btn-mac.png") no-repeat;
  background-size: 100% 100%;
  width: 156px;
  height: 52px;
}
.navbar a {
  cursor: pointer;
}
</style>
