<template>
<div class="container" id="appComponent" >


  <section>
    <h4></h4>
  </section>

  <section>
    <div class="card">
      <div class="card-info">
        <h1 id="card-info-title">{{ currentCard.title }}</h1>
        <p id="card-info-desc">{{ currentCard.desc }}</p>
        <a href="#">
          <p>More details</p>
          <svg viewBox="0 0 20 10">
            <line x1="0" y1="5" x2="20" y2="5" />
            <line x1="15" y1="0" x2="20" y2="5" />
            <line x1="15" y1="10" x2="20" y2="5" />
          </svg>
        </a>
      </div>
      <div class="card-photo">
        <div id="mask-1" class="mask"></div>
        <div id="mask-2" class="mask"></div>
        <a href="#" @click="nextCard">
          <p>Next</p>
          <svg viewBox="0 0 20 10">
            <line x1="0" y1="5" x2="20" y2="5" />
            <line x1="15" y1="0" x2="20" y2="5" />
            <line x1="15" y1="10" x2="20" y2="5" />
          </svg>
        </a>
        <img :src="currentCard.photo">
      </div>
    </div>
  </section>
</div>
</template>

<script>
import gsap from "gsap";

export default {
  name: 'HelloWorld',
  data() {
    return {
      cards: [
        {
          id: 1,
          title: "Cincinnati",
          desc:
            "In different heights and shapes, the four versions of Floema low tables offer a variety of surfaces to satisfy different needs and uses in a contract environment, from work to moments of relaxation.",
          photo:
            "https://images.unsplash.com/photo-1649011327045-624a1bd2c3e7?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=853&q=80"
        },
        {
          id: 2,
          title: "Daytona",
          desc:
            "The Circle Coffee table from Wendelbo emulates almost a visual trick. A frame where mass and gravity is suspended, and the slim and delicate structure support the marble top, like a hovering platform.",
          photo:
            "https://images.unsplash.com/photo-1615529182904-14819c35db37?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=880&q=80"
        },
        {
          id: 3,
          title: "Indiana",
          desc:
            "With an appearance that is at once light and elegant, the Workshop Coffee Table fits perfectly into any living room, serving as a traditional coffee table as well as side table.",
          photo:
            "https://images.unsplash.com/flagged/photo-1588262516915-e342186ecdf6?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=880&q=80"
        },
        {
          id: 4,
          title: "Amarillo",
          desc:
            "Made from sustainably sourced solid American Oak, the Duo Table is composed of two seperate tops joined together on one side. The tops are solid and carved out to create a gentle lip. ",
          photo:
            "https://images.unsplash.com/photo-1622372738946-62e02505feb3?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=832&q=80"
        }
      ],
      currentNum: 0
    };
  },
  computed: {
    currentCard() {
      return this.cards[this.currentNum];
    }
  },
  methods: {
    playFoward() {
      let tl = gsap.timeline({
        defaults: {
          duration: 0.7,
          ease: "sine.out"
        },
        onComplete: () => {
          this.playReverse();
          if (this.currentNum >= 3) {
            this.currentNum = 0;
          } else {
            this.currentNum++;
          }
        }
      });
      tl.to("#mask-1", {
        yPercent: 100,
        scaleY: 1.4
      })
        .to(
          "#mask-2",
          {
            yPercent: -100,
            scaleY: 1.4
          },
          "<"
        )
        .to(
          "#card-info-title",
          {
            clipPath: `polygon(0 0, 100% 0, 100% 0%, 0% 0%)`
          },
          "<0.4"
        )
        .to(
          "#card-info-desc",
          {
            clipPath: `polygon(0 0, 100% 0, 100% 0%, 0% 0%)`
          },
          "<0.3"
        );
    },
    playReverse() {
      let tl = gsap.timeline({
        defaults: {
          duration: 0.7,
          ease: "sine.in"
        }
      });
      tl.to("#mask-1", {
        yPercent: -100,
        scaleY: 1.4
      })
        .to(
          "#mask-2",
          {
            yPercent: 100,
            scaleY: 1.4
          },
          "<"
        )
        .to(
          "#card-info-title",
          {
            clipPath: `polygon(0 0, 100% 0, 100% 100%, 0% 100%)`
          },
          "<0.2"
        )
        .to(
          "#card-info-desc",
          {
            clipPath: `polygon(0 0, 100% 0, 100% 100%, 0% 100%)`
          },
          "<0.3"
        );
    },
    nextCard() {
      this.playFoward();
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Allura&family=Poppins:wght@300&display=swap");


* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

:root {
  --green: #ecfaec;
  --dark-green: #166639;
  --white: #ffffff;
  --black: #202020;
}

body {
  min-height: 100vh;
  display: grid;
  place-items: center;
  font-family: "Poppins", sans-serif;
  background-color: #c46c92;
  background-image: url("https://www.transparenttextures.com/patterns/absurdity.png");
  color: var(--black);
  
}

ul {
  list-style: none;
}

a {
  text-decoration: none;
  color: inherit;
}

.container {
  width: 100%;
  max-width: 900px;
  display: block;
  flex-grow: 0;
  flex-shrink: 1;
  flex-basis: auto;
  align-self: auto;
  order: 0;
}

header {
  padding: 2em 1em;
  display: grid;
  grid-template-columns: 100px 1fr;
  align-items: center;
}
header h1 {
  font-family: "Allura", serif;
  color: #deb8bc;
}
header ul {
  display: flex;
}
header li {
  margin-right: 3em;
  font-size: 0.85rem;
  font-weight: bold;
}

section {
  width: 100%;
  padding: 1em;
}

section h4 {
  opacity: 0.8;
}

li.active {
  color: #deb8bc;
  border-bottom: 1px solid #deb8bc;
}

.card {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-auto-rows: auto;
  background-color: var(--white);
  box-shadow: rgba(255, 255, 255, 0.1) 0px 1px 1px 0px inset,
    rgba(50, 50, 93, 0.25) 0px 50px 100px -20px,
    rgba(0, 0, 0, 0.3) 0px 30px 60px -30px;
}

.card-info {
  display: grid;
  grid-template-rows: repeat(3, 1fr);
  padding: 1em 2em;
}
.card-info h1 {
  font-family: "Allura", serif;
  font-size: 5rem;
  color: #deb8bc;
  align-self: center;
  clip-path: polygon(0 0, 100% 0, 100% 100%, 0% 100%);
}
.card-info p {
  font-size: 0.8rem;
  font-weight: bold;
  align-self: center;
  clip-path: polygon(0 0, 100% 0, 100% 100%, 0% 100%);
  line-height: 22px;
}
.card-info a {
  display: grid;
  grid-template-columns: max-content 20px;
  align-items: center;
  column-gap: 7px;
  color: #deb8bc;
  font-size: 0.85rem;
  font-weight: bold;
  align-self: center;
  justify-self: flex-end;
  transform: translateX(0px);
  transition: transform 0.3s 0.1s ease-out;
}
.card-info a:hover {
  transform: translateX(5px);
}
.card-info a:hover svg {
  transform: translateX(5px);
}
.card-info svg {
  width: 20px;
  height: 10px;
  transform: translateX(0px);
  transition: transform 0.3s ease-out;
}
.card-info svg line {
  stroke: #deb8bc;
}

.card-photo {
  width: 450px;
  object-fit: cover;
  position: relative;
  overflow: hidden;
}
.card-photo img {
  display: block;
  max-width: 100%;
  aspect-ratio: 1/1;
}
.card-photo a {
  display: grid;
  grid-template-columns: max-content 20px;
  align-items: center;
  column-gap: 7px;
  color: var(--white);
  font-size: 1rem;
  font-weight: bold;
  letter-spacing: 1px;
  align-self: flex-start;
  transform: translateX(0px);
  transition: transform 0.3s 0.1s ease-out;
  position: absolute;
  z-index: 10;
  bottom: 5%;
  right: 8%;
}
.card-photo a:hover {
  transform: translateX(5px);
}
.card-photo a:hover svg {
  transform: translateX(5px);
}
.card-photo svg {
  width: 20px;
  height: 10px;
  transform: translateX(0px);
  transition: transform 0.3s ease-out;
}
.card-photo svg line {
  stroke: var(--white);
  stroke-width: 2;
}
.card-photo >>> .mask {
  position: absolute;
  top: 0;
  height: 100%;
  width: 50%;
  z-index: 5;
  background-color: #f5eaec;
}
#mask-1 {
  left: 0;
  transform: translateY(-100%);
}
#mask-2 {
  right: 0;
  transform: translateY(100%);
}

@media (max-width: 600px) {
  .card {
    grid-template-columns: 1fr;
    justify-items: center;
  }

  .card-info {
    order: 2;
    height: 400px;
  }
  .card-photo {
    width: 100%;
    order: 1;
  }

  .card-photo img {
    width: 100%;
  }

  .card-photo .mask {
    height: 100%;
  }
}

@media (max-width: 500px) {
  header {
    padding: 1em;
    grid-template-columns: 1fr 1fr;
    align-items: flex-start;
  }
  header ul {
    flex-direction: column;
  }
  header li {
    width: min-content;
    margin-right: 0;
  }
  .card-info h1 {
    font-size: 3rem;
  }
}

</style>
