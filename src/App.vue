<script setup>
  import { ref, getCurrentInstance } from "vue";
  import { vue3dLoader } from "vue-3d-loader";

  const { proxy } = getCurrentInstance();
  
  //Page event
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
  
  let btnSmallMenuStatus = false;
  let smallMenuActive = ref(btnSmallMenuStatus);
  const btnMenuSmallClick = ($event) => {
    smallMenuActive.value = !btnSmallMenuStatus;
    btnSmallMenuStatus = !btnSmallMenuStatus;
  };

  /**
   * Xử lý các vấn đề view tàu
   */
  var ships = [
    {Id: 1, Name: "Apollo I", SubName: "Common", Class: "ship-apollo", Path3D: "/3d_model/ship_apollo/ship_apollo.gltf", Description: "The first generation of spaceships was created to protect the earth from alien attack. Named after the god of light. Apollo I ushered in the era of human space warfare. Light, high speed and easy to use. Apollo I is usually used for scouting missions." , Mass: 800, Weight: 250, Speed: 7.9, Health: 100, Attach: 100, Shield: 100},
    {Id: 2, Name: "Athena III", SubName: "Uncommon", Class: "ship-athena", Path3D: "/3d_model/ship_athena/ship_athena.gltf", Description: "The 3rd generation spacecraft was built by the Earth Protection Organization. Named after the goddess of wisdom. This is the upgraded generation of Apollo I with improved engines and weapons and stronger protective shield. Athena II nowadays are mass-produced to protect the earth." , Mass: 800, Weight: 250, Speed: 7.9, Health: 120, Attach: 150, Shield: 100},
    {Id: 3, Name: "Ares V", SubName: "Rare", Class: "ship-ares", Path3D: "/3d_model/ship_ares/ship_ares.gltf", Description: "This spaceship is equipped with medium firepower, high frequency cannon. Junador Lidona - The former director of EPO personally designed it after only 2 year of the alien attack event. Unlike the others, this is a generation of spacecraft built for special missions. Named after the god of war, this spaceship is a nightmare for enemies across the galaxy." , Mass: 700, Weight: 300, Speed: 11.2, Health: 150, Attach: 150, Shield: 150},
    {Id: 4, Name: "Poseidon VII", SubName: "Epic", Class: "ship-poseidon", Path3D: "/3d_model/ship_poisedon/ship_poisedon.gltf", Description: "The 7th generation spaceship. Named after the god of the seas. Equipped with supersonic jet engines and powerful weapons, it is easy to fight large numbers of enemies." , Mass: 600, Weight: 350, Speed: 11.2, Health: 150, Attach: 180, Shield: 180},
    {Id: 5, Name: "Zeus X", SubName: "Legend", Class: "ship-zeus", Path3D: "/3d_model/ship_zeus/ship_zeus.gltf", Description: "The most modern generation of spaceships. Named after the King of the gods and ruler of Mount Olympus; god of the sky, lightning, thunder, law, order and justice. Crafted by Earth Protection Organization (EPO). Equipped with the best weapons and armor, high technology to Stealth with enemies, these spaceships are able to fight the most powerful enemies." , Mass: 500, Weight: 450, Speed: 16.6, Health: 200, Attach: 200, Shield: 200}
  ];
  var shipActive = ref(ships[0]);
  const position = ref();
  position.value = [
    { x: 0, y: 0, z: 0 },
    { x: 100, y: 100, z: 100 },
  ];
  const rotation = ref();
  rotation.value = [
    { x: 0, y: 0, z: 0 },
    { x: 10, y: 1, z: 1 },
  ];
  const lights = [
    {
      type: "AmbientLight",
      color: "#fff",
    },
    {
      type: "DirectionalLight",
      position: { x: 50, y: 5, z: 50 },
      color: "#fff",
      intensity: 1,
    },
    {
      type: "PointLight",
      color: "#fff",
      position: { x: 100, y: -100, z: 50 },
      intensity: 1
    },
    {
      type: "HemisphereLight",
      skyColor: "#fff",
      groundColor: "#000000",
      position: { x: 200, y: -200, z: 100 }
    }
  ];
  const onClickShip = (event, ship) => {
    shipActive.value = ship;
  };


  /**
   * Partner
   */
  var partners = [
    {Id: 1, Name: 'Binance', Class: "partner-binance"},
    {Id: 2, Name: 'Unity', Class: "partner-unity"},
    {Id: 3, Name: 'CoinMarketCap', Class: "partner-coinmarketcap"},
    {Id: 4, Name: 'CoinGecko', Class: "partner-coingecko"}
  ];



</script>

<template>

  <div class="bg landing-page">
    <nav class="navbar navbar-expand-lg text-uppercase fixed-top" id="mainNav">
      <div class="container">
        <a class="navbar-brand logo" @click="menuClick('home')"></a>
        <button
          class="navbar-toggler text-uppercase font-weight-bold text-white rounded"
          type="button"
          @click="btnMenuSmallClick($event)"> 
          <div class="btn-menu-bar"></div>  
          <div class="btn-menu-bar"></div>  
          <div class="btn-menu-bar"></div>  
        </button>
        <div :class="['collapse navbar-collapse',{'small-menu-show': smallMenuActive}]" id="navbarResponsive">
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
                >PARTNER</a
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
              <div class="what-ship what-ship-one ship-transfer-1"></div>
              <div class="what-ship what-ship-two ship-transfer-2"></div>
              <div class="what-ship what-ship-three ship-transfer-3"></div>
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
            <div class="ship-img-container col-12 col-sm-12 col-md-12 col-lg-12 col-xl-8 col-xxl-7 p-0">
                <div class="ship-img-view">
                  <!-- <div :class="['ship-image-bg', shipActive.Class]"></div> -->
                  <div class="ship-image-bg">
                    <vue3dLoader
                      :height="350"
                      :filePath="shipActive.Path3D"
                      backgroundColor="rgba(255, 255, 255)"
                      :backgroundAlpha="0.25"
                      :camera-position="{x: 0, y: 0, z: 0}"
                      :rotation="rotation"
                      :position="position"
                      :lights="lights"
                    ></vue3dLoader>
                  </div>
                  
                </div>
                <div class="ship-img-list">
                  <div :class="['item', {'active': ship.Id == shipActive.Id}]" v-for="(ship, index) in ships" @click="onClickShip($event, ship)" :key="index">
                    <div :class="['ship-img-item', ship.Class]" :title="ship.Name"></div>
                  </div>
                </div>
            </div>
            <div class="ship-spec-container col-12 col-sm-12 col-md-12 col-lg-12 col-xl-4 col-xxl-4">
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
                      <div class="spec-detail-numeral">{{shipActive.Speed}} km/s</div>
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
            <div class="roadmap-box col-12 col-sm-12 col-md-6 col-lg-4 col-xl-3 col-xxl-3">
              <div class="roadmap-box-container arrow_box">
                <div class="roadmap-box-content">
                  <div class="roadmap-box-title cl-orange">The beginning of the universe</div>
                  <div class="roadmap-box-info">
                    <div class="rbi-item">
                      <div class="rbi-item-title">-</div>
                      <div class="rbi-item-info">Story idea, NFT and game built</div>
                    </div>
                    <div class="rbi-item">
                      <div class="rbi-item-title">-</div>
                      <div class="rbi-item-info">Initialize website, create smart contract</div>
                    </div>
                    <div class="rbi-item">
                      <div class="rbi-item-title">-</div>
                      <div class="rbi-item-info">Audit the contract and KYC by ContractChecker</div>
                    </div>
                    <div class="rbi-item">
                      <div class="rbi-item-title">-</div>
                      <div class="rbi-item-info">Release testnet game version</div>
                    </div>
                    <div class="rbi-item">
                      <div class="rbi-item-title">-</div>
                      <div class="rbi-item-info">Launch the IGO on Website</div>
                    </div>
                    <div class="rbi-item">
                      <div class="rbi-item-title">-</div>
                      <div class="rbi-item-info">Launch the ILO on Website</div>
                    </div>
                    <div class="rbi-item">
                      <div class="rbi-item-title">-</div>
                      <div class="rbi-item-info">Listing on Pancakeswap</div>
                    </div>
                    <div class="rbi-item">
                      <div class="rbi-item-title">-</div>
                      <div class="rbi-item-info">Listing on Coinmarketcap and Coingecko</div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
            <div class="roadmap-box col-12 col-sm-12 col-md-6 col-lg-4 col-xl-3 col-xxl-3">
              <div class="roadmap-box-container arrow_box">
                <div class="roadmap-box-content">
                  <div class="roadmap-box-title cl-orange">Welcome new users</div>
                  <div class="roadmap-box-info">
                    <div class="rbi-item">
                      <div class="rbi-item-title">-</div>
                      <div class="rbi-item-info">Run marketing program</div>
                    </div>
                    <div class="rbi-item">
                      <div class="rbi-item-title">-</div>
                      <div class="rbi-item-info">Release Battle (PvE) features.</div>
                    </div>
                    <div class="rbi-item">
                      <div class="rbi-item-title">-</div>
                      <div class="rbi-item-info">Open NFT market</div>
                    </div>
                    <div class="rbi-item">
                      <div class="rbi-item-title">-</div>
                      <div class="rbi-item-info">Expand partnerships, run marketing programs</div>
                    </div>
                    <div class="rbi-item">
                      <div class="rbi-item-title">-</div>
                      <div class="rbi-item-info">Release PVP features.</div>
                    </div>
                    <div class="rbi-item">
                      <div class="rbi-item-title">-</div>
                      <div class="rbi-item-info">Upgrade the game (characters, equipments, features,...)</div>
                    </div>
                    <div class="rbi-item">
                      <div class="rbi-item-title">-</div>
                      <div class="rbi-item-info">CEXs listing</div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
            <div class="roadmap-box col-12 col-sm-12 col-md-6 col-lg-4 col-xl-3 col-xxl-3">
              <div class="roadmap-box-container arrow_box">
                <div class="roadmap-box-content">
                  <div class="roadmap-box-title cl-orange">Ecosystem development</div>
                  <div class="roadmap-box-info">
                    <div class="rbi-item">
                      <div class="rbi-item-title">-</div>
                      <div class="rbi-item-info">Global community events</div>
                    </div>
                    <div class="rbi-item">
                      <div class="rbi-item-title">-</div>
                      <div class="rbi-item-info">More Marketing push on Influencers, youtube channel</div>
                    </div>
                    <div class="rbi-item">
                      <div class="rbi-item-title">-</div>
                      <div class="rbi-item-info">New feature to use SXC token</div>
                    </div>
                    <div class="rbi-item">
                      <div class="rbi-item-title">-</div>
                      <div class="rbi-item-info">SpaceXCyber hackathon</div>
                    </div>
                    <div class="rbi-item">
                      <div class="rbi-item-title">-</div>
                      <div class="rbi-item-info">Contract audit by CertiK</div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
            <div class="roadmap-box col-12 col-sm-12 col-md-6 col-lg-4 col-xl-3 col-xxl-3">
              <div class="roadmap-box-container arrow_box">
                <div class="roadmap-box-content">
                  <div class="roadmap-box-title cl-orange">METAVERSE</div>
                  <div class="roadmap-box-info">
                    <div class="rbi-item">
                      <div class="rbi-item-title">-</div>
                      <div class="rbi-item-info">Launch second game</div>
                    </div>
                    <div class="rbi-item">
                      <div class="rbi-item-title">-</div>
                      <div class="rbi-item-info">Game-branded metaverse project</div>
                    </div>
                    <div class="rbi-item">
                      <div class="rbi-item-title">-</div>
                      <div class="rbi-item-info">API development for other platforms</div>
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
            <span class="title-border"></span><span class="title-content">TOKENNOMICS</span>
          </div>
          <div class="mt-5 tokenomic-container">
            <div class="bg-tokenomic"></div>
          </div>
        </div>
      </section>
      <!-- Partner Section-->
      <section class="page-section vh-100" id="partner">
        <div class="container text-white">
          <div class="title">
            <span class="title-border"></span
            ><span class="title-content">Partner</span>
          </div>
          <div class="row mt-5 page-section-content">
            <div class="partner-box col-xxl-3 col-xl-3 col-lg-4 col-md-6 col-sm-12 col-12" v-for="(par, index) in partners" :key="index">
              <div class="partner-box-content">
                <div :class="['partner-box-img', par.Class]" :title="par.Name"></div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
    <div class="footer-container">
      <div class="footer-box container">
        <footer class="footer-content">
          <div class="join-title">JOIN OUR COMMUNITY</div>
          <div class="social-container">
            <ul class="nav list-unstyled d-flex col-xxl-12 col-xl-12 col-lg-12 col-md-12 col-12">
              <li class=""><a class="text-muted" href="https://twitter.com/SpaceXCyber" target="_blank"><svg class="social-ic twitter-ic"></svg></a></li>
              <li class=""><a class="text-muted" href="#facebook" target="_blank"><svg class="social-ic facebook-ic"></svg></a></li>
              <li class=""><a class="text-muted" href="https://discord.gg/keRq8UX5" target="_blank"><svg class="social-ic discord-ic"></svg></a></li>
              <li class=""><a class="text-muted" href="https://t.me/SpaceXCyberWorld" target="_blank"><svg class="social-ic telegram-ic"></svg></a></li>
            </ul>
          </div>
          <div class="footer-intro">
            SpaceX Cyber is an MMORPG built on blockchain, where players control spaceships to explore, fight and win rewards. <br>
            Experience space exploration, massive PvP and PvE battles, and a thriving player economy in an ever-expanding sandbox. <br>
            Take part in many professions and activities in the game, including war, piracy, trade and exploration, with hundreds of thousands of other players.
          </div>
          <div class="footer-copy-right">
            Copyright © 2021-2022, SpacexCyber. All Rights Reserved
          </div>
        </footer>
      </div>
    </div>
  </div>
</template>
