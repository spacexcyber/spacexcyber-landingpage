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

/**
 * Xử lý các vấn đề view tàu
 */
var ships = [{Id: 1, Name: "Alpha", SubName: "Reconnaissance,  Battleship", ImgPath: "/src/assets/images/ships/ship_01.svg", Description: "Alpha's advantages are high mobility and very low cost. Designed to be an investigative and combat job in any situation. Alpha is by far the most widely used battleship worldwide." , Mass: 500, Weight: 250, Speed: 300, Health: 1000, Attach: 500, Shield: 500},
{Id: 2, Name: "Beta", SubName: "Reconnaissance,  Battleship", ImgPath: "/src/assets/images/ships/ship_02.svg", Description: "Alpha's advantages are high mobility and very low cost. Designed to be an investigative and combat job in any situation. Alpha is by far the most widely used battleship worldwide." , Mass: 600, Weight: 350, Speed: 200, Health: 1500, Attach: 500, Shield: 500},
{Id: 3, Name: "Gamma", SubName: "Reconnaissance,  Battleship", ImgPath: "/src/assets/images/ships/ship_03.svg", Description: "Alpha's advantages are high mobility and very low cost. Designed to be an investigative and combat job in any situation. Alpha is by far the most widely used battleship worldwide." , Mass: 700, Weight: 150, Speed: 700, Health: 800, Attach: 400, Shield: 600},
{Id: 4, Name: "Delta", SubName: "Reconnaissance,  Battleship", ImgPath: "/src/assets/images/ships/ship_04.svg", Description: "Alpha's advantages are high mobility and very low cost. Designed to be an investigative and combat job in any situation. Alpha is by far the most widely used battleship worldwide." , Mass: 800, Weight: 450, Speed: 320, Health: 1200, Attach: 300, Shield: 500}];
var shipActive = ref(ships[0]);

const onClickShip = (event, ship) => {
  shipActive.value = ship;
};

var partners = [{Id: 1, Name: 'Binance', ImgPath: "/src/assets/images/ships/binance.svg"},
{Id: 2, Name: 'Coinall', ImgPath: "/src/assets/images/ships/coinall.svg"},
{Id: 3, Name: 'Bybit', ImgPath: "/src/assets/images/ships/bybit.svg"},
{Id: 4, Name: 'Okex', ImgPath: "/src/assets/images/ships/okex.svg"},
{Id: 5, Name: 'Kucoin', ImgPath: "/src/assets/images/ships/kucoin.svg"},
{Id: 6, Name: 'Near', ImgPath: "/src/assets/images/ships/near.svg"},
{Id: 7, Name: 'Unity', ImgPath: "/src/assets/images/ships/unity.svg"},
{Id: 8, Name: 'AWS', ImgPath: "/src/assets/images/ships/aws.svg"}]
</script>

<template>

  <div class="bg landing-page">
    <nav class="navbar navbar-expand-lg text-uppercase fixed-top" id="mainNav">
      <div class="container">
        <a class="navbar-brand logo" @click="menuClick('home')"></a>
        <button
          class="navbar-toggler text-uppercase font-weight-bold text-white rounded"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarResponsive"
          aria-controls="navbarResponsive"
          aria-label="Toggle navigation"
          aria-expanded="false"> Menu <span class="navbar-toggler-icon"></span> </button>
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
                :class="activeMenu === 'spacexcyber' ? 'active' : ''"
                @click="menuClick('spacexcyber')"
                >SpaceXCyber</a
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
                class="nav-link py-3 px-0 "
                :class="activeMenu === 'partner' ? 'active' : ''"
                @click="menuClick('partner')"
                >PARTNER AND BACKER</a
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
      <section class="page-section masthead text-white text-center d-flex align-items-center vh-100 " id="home">
        <div class="container d-flex align-items-center flex-column">
          <!-- Masthead Heading-->
          <h1 class="masthead-heading text-uppercase mb-0">
            METAVERSE UNIVERSE
          </h1>
          <h1 class="masthead-heading text-uppercase mb-0">THE #1 SPACE MMO</h1>
          <div class="masthead-subheading font-weight-light mb-0 row">
            <div class="down-box col-xxl-4 col-xl-4 col-lg-4 col-md-4 col-sm-12 col-12">
              <a class="btn btn-xl spx-btn btn-win" href="#"> </a>
            </div>
            <div class="down-box col-xxl-4 col-xl-4 col-lg-4 col-md-4 col-sm-12 col-12">
              <a class="btn btn-xl spx-btn btn-apk" href="#"> </a>
            </div>
            <div class="down-box col-xxl-4 col-xl-4 col-lg-4 col-md-4 col-sm-12 col-12">
              <a class="btn btn-xl spx-btn btn-mac" href="#"> </a>
            </div>
          </div>
          <div class="row mt-5">
            <div class="col">
              <div class="lead">
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
      <section class="page-section vh-100" id="spacexcyber">
        <div class="container text-white">
          <div class="title">
            <span class="title-border"></span
            ><span class="title-content"
              >What is Space<span class="cl-orange">X</span>Cyber</span
            >
          </div>
          <div class="row page-what-content">
            <div class="col what-content">
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
            <div class="col what-ship-container">
              <div class="what-ship-one ship-transfer-1"></div>
              <div class="what-ship-two ship-transfer-2"></div>
              <div class="what-ship-three ship-transfer-3"></div>
            </div>
          </div>
        </div>
      </section>
      <!-- spaceship Section-->
      <section class="page-section vh-100 spaceship-overview" id="spaceship">
        <div class="container text-white">
          <div class="section-title">
            <div class="title">
              <span class="title-border"></span><span class="title-content">SPACESHIP OVERVIEW</span>
            </div>
            <div class="sub-title fs-subtitle">
              A SMALL SAMPLE OF THE 1000+ NFT YOU CAN FLY
            </div>
          </div>
          
          <div class="row mt-1 page-section-content">
            <div class="ship-img-container">
                <div class="ship-img-view">
                  <div class="ship-image-bg" :style="{backgroundImage: `url(${shipActive.ImgPath})`}"></div>
                </div>
                <div class="ship-img-list">
                  <div :class="['item', {'active': ship.Id == shipActive.Id}]" v-for="(ship, index) in ships" @click="onClickShip($event, ship)" :key="index">
                    <div class="ship-img-item" :style="{backgroundImage: `url(${ship.ImgPath})`}">{{ship.Name}}</div>
                  </div>
                </div>
            </div>
            <div class="ship-spec-container">
              <div class="ship-spec-content">
                <div class="spec-row spec-name">
                    <div class="ship-name fs-subtitle f-uppper">{{shipActive.Name}}</div>
                    <div class="ship-subname cl-orange f-uppper">{{shipActive.SubName}}</div>
                </div>
                <div class="spec-row spec-description">
                    {{shipActive.Description}}
                </div>
                <div class="spec-row spec-overview">
                    <div class="spec-detail">
                      <div class="spec-detail-title cl-orange">MASS</div>
                      <div class="spec-detail-numeral">{{shipActive.Mass}} t</div>
                    </div>
                    <div class="spec-detail">
                      <div class="spec-detail-title cl-orange">WEIGHT</div>
                      <div class="spec-detail-numeral">{{shipActive.Weight}} m3</div>
                    </div>
                    <div class="spec-detail">
                      <div class="spec-detail-title cl-orange">SPEED</div>
                      <div class="spec-detail-numeral">{{shipActive.Speed}} m/s</div>
                    </div>
                </div>
                <div class="spec-row spec-overview">
                    <div class="spec-detail">
                      <div class="spec-detail-title cl-orange">HEALTH</div>
                      <div class="spec-detail-numeral">{{shipActive.Health}}</div>
                    </div>
                    <div class="spec-detail">
                      <div class="spec-detail-title cl-orange">ATTACK</div>
                      <div class="spec-detail-numeral">{{shipActive.Attach}}</div>
                    </div>
                    <div class="spec-detail">
                      <div class="spec-detail-title cl-orange">SHIELD</div>
                      <div class="spec-detail-numeral">{{shipActive.Shield}}</div>
                    </div>
                </div>

              </div>
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
            <!-- <div class="col">
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
            </div> -->
            <div class="roadmap-box col-12 col-sm-12 col-md-6 col-lg-4 col-xl-3 col-xxl-2">
              <div class="roadmap-box-container arrow_box">
                <div class="roadmap-box-content">
                  <div class="roadmap-box-title cl-orange">2022-Q1</div>
                  <div class="roadmap-box-info">
                    <div class="rbi-item">
                      <div class="rbi-item-title"></div>
                      <div class="rbi-item-info"></div>
                    </div>
                  </div>
                </div>
              </div>
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
            <!-- <div class="col">
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
            </div> -->
            <div class="partner-box col-xxl-3 col-xl-3 col-lg-4 col-md-6 col-sm-12 col-12" v-for="(par, index) in partners" :key="index">
              <div class="partner-box-content">
                <div class="partner-box-img" :style="{backgroundImage: `url(${par.ImgPath})`}" :title="par.Name"></div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>
