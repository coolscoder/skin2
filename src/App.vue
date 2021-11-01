<template>
  <div container>
    <fieldset>
      <legend>This is Top</legend>
      <div data-container>
        <img data-avatar :src="linkdrip.profile.image" />
        <h1 data-username v-text="linkdrip.profile.name.text"></h1>
        <p data-description v-text="linkdrip.profile.description.text"></p>
        <ul data-links>
          <!-- <li
            data-link-container
            v-for="(link, index) in linkdrip.links"
            v-bind:key="index"
            v-on:click = "handleExtend(index)"
          >
            <LinkItem :link="link" />
            <ExtendedItem v-if="linkdrip.extends[index]" :extends="link.extends" />
          </li> -->
          <!-- <div class="cube"> -->
            <div class="side top"></div>
            <div class="front-view">
              <div class="side left"></div>
              <div class="side front"></div>
            </div>
          <!-- </div> -->
        </ul>
      </div>
    </fieldset>
    <fieldset left>
      <legend>This is Left</legend>
    </fieldset>
    <fieldset bottom>
      <legend>This is Bottom</legend>
    </fieldset>
    <fieldset right>
      <legend>This is Right</legend>
    </fieldset>
  </div>
</template>

<script>
  // import LinkItem from './components/LinkItem.vue'
  // import ExtendedItem from './components/ExtendedItem.vue'

  export default {
    name: 'App',
    components: {
      // LinkItem,
      // ExtendedItem,
    },
    data: () => ({
      animate: false,
      linkdrip:{
        skin: 'SKIN_NAME',
        profile:{
          image: "https://smhlancers.org/wp-content/uploads/2016/06/profile-placeholder-300x300.png",
          name:{
            text: "John Doe"
          },
          description: {
            text: "This is my description"
          }
        },
        extends: [],
        links: [
          {
            url: "http://google.com",
            label: "This is a link",
            extends: [
              {
                url: "http://google.com",
                label: "This is another link",
              },
              {
                url: "http://google.com",
                label: "This is another link",
              },
              {
                url: "http://google.com",
                label: "This is another link",
              },
            ]
          },
          {
            url: "http://google.com",
            label: "This is a link",
            extends: [
              {
                url: "http://google.com",
                label: "This is another link",
              },
              {
                url: "http://google.com",
                label: "This is another link",
              },
              {
                url: "http://google.com",
                label: "This is another link",
              },
            ]
          },
          {
            url: "http://google.com",
            label: "This is a link",
            extends: [
              {
                url: "http://google.com",
                label: "This is another link",
              },
              {
                url: "http://google.com",
                label: "This is another link",
              },
              {
                url: "http://google.com",
                label: "This is another link",
              },
            ]
          },
          {
            url: "http://google.com",
            label: "This is a link",
            extends: [
              {
                url: "http://google.com",
                label: "This is another link",
              },
              {
                url: "http://google.com",
                label: "This is another link",
              },
              {
                url: "http://google.com",
                label: "This is another link",
              },
            ]
          }
        ]
      }
    }),
    created() {
      this.$data.linkdrip.links.forEach(() => {
        this.$data.linkdrip.extends.push(false)
      });
    },
    methods: {
      handleExtend(index) {
        if(this.$data.linkdrip.extends[index]) {
          this.$data.linkdrip.extends[index] = false
        } else {
          this.$data.linkdrip.extends[index] = true
        }
      }
    },
  }
</script>

<style lang="scss">
  body {
    background: #fff;
    color: #fff;
    font-family: Helvetica;
    text-align: center;
    margin: 0;
  }
  fieldset {
    border: 20px solid transparent; 
    border-top-color: #fff; 
    box-sizing: border-box; 
    grid-area: 1 / 1; 
    width: inherit; 
    padding: 0;
    margin: 0;
  }
  legend {
    color: black;
    animation: marginMove 4s infinite alternate;

    @keyframes marginMove {
      0%{
        margin-left: -100px;
      }
      100% {
        margin-left: 100px;
      }
    }
  }
  [left] {
    transform: rotate(-90deg) translateX(50vh) translateX(20px) translateY(-50vh) translateY(20px);
    width: 100vh;
  }
  [bottom] {
    transform: rotate(180deg) translateY(80px);
  }
  [right] {
    // transform: rotate(90deg) translateX(-50vh) translateX(-100px) translateY(-50vw);
    transform: rotate(90deg) translateX(-50vh) translateX(-100px) translateY(-100vw) translateY(50vh) translateY(20px);
    width: 100vh;
  }
  [container] {
    background-color: #fff;
    border-radius: 20px;
    height: 100vh;
    overflow: hidden;
  }
	[data-container] {
		padding: 0 1rem;
    background-color: #000;
    border-radius: 20px;
    height: calc(100vh - 40px);
    overflow-x: hidden;
    overflow-y: scroll;
	}
	[data-avatar] {
		position: relative;
		z-index: 5;
		width: 100%;
		max-width: 5.5rem;
		margin: 3rem auto 0.5rem;
		border-radius: 100rem;
	}
	[data-username] {
		position: relative;
		z-index: 5;
		font-size: 1.3rem;
		margin: 0 0 0.25rem;
	}
	[data-description]{
		position: relative;
		z-index: 5;
		font-size: 1rem;
	}
	[data-links]{
		margin: 2rem 0;
    padding: 0;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
		li{
			margin-top: 1rem;
      border: 1px solid #fff; 
      display: flex;
      flex-direction: column;
      align-items: center;
      cursor: pointer;
      border-radius: 6px;
			a {
				display: block;
				font-size: 1rem;
				position: relative;
				color: inherit;
        margin: 1rem 0;
				span{
					position: relative;
					z-index: 1;
				}
				[data-button-icon]{
					font-size: 1.3rem;
					color: #fff;
					position: absolute;
					top: 50%;
					left: 1.5rem;
					transform: translate3d(0,-50%,0);
				}
			}
		}
    // .cube {
      // position: absolute;
      // top: 50%;
      // left: 50%;
      // transform-style: preserve-3d;
      // transform: rotateX(180deg);
      // background-color: red;
      .side {
        width: 100%;
        height: 100%;
        border: 2px solid white;
        background: transparent;
      }
      .front-view {
        display: flex;
        justify-content: center;
        align-items: center;
        .left {
          transform: rotateX(-45deg) rotateY(-45deg) translateX(12px) translateY(-27px);
          width: 50px;
          height: 72px;
          background-color: aqua;
        }
        .front {
          transform-origin: bottom;
          background: greenyellow;
          width: 200px;
          height: 50px;
        }
      }
      .top {
        width: 246px;
        height: 66px;
        transform: rotateX(289deg) rotateY(167deg) rotate(33deg) translateX(45px) translateY(86px);
        transform-origin: center;
        background: red;
      }
    // }
    
  }
</style>
