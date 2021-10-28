<template>
  <div container>
    <!-- <div data-container>
      <img data-avatar :src="linkdrip.profile.image" />
      <h1 data-username v-text="linkdrip.profile.name.text"></h1>
      <p data-description v-text="linkdrip.profile.description.text"></p>
      <ul data-links>
        <li
          data-link-container
          v-for="(link, index) in linkdrip.links"
          v-bind:key="index"
          v-on:click = "handleExtend(index)"
        >
          <LinkItem :link="link" />
          <ExtendedItem v-if="linkdrip.extends[index]" :extends="link.extends" />
        </li>
      </ul>
    </div> -->
    <div textborder>
      <slot v-for="n in 10" :key="n">{{linkdrip.profile.name.text+' &middot;'}}</slot>
    </div>
  </div>
</template>

<script>
  // import LinkItem from './components/LinkItem.vue'
  // import ExtendedItem from './components/ExtendedItem.vue'

  export default {
    name: 'App',
    // components: {
    //   LinkItem,
    //   ExtendedItem,
    // },
    data: () => ({
      search: new URLSearchParams(window.location.search),
      visible: false,
      linktree: false,
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
    mounted() {
      // this.startAnimations();
      this.startEmblem('[textborder]');
    },
    methods: {
      handleExtend(index) {
        if(this.$data.linkdrip.extends[index]) {
          this.$data.linkdrip.extends[index] = false
        } else {
          this.$data.linkdrip.extends[index] = true
        }
      },
      startAnimations() {
        this.animate = true
      },
      startEmblem(el, str) {
        var element = document.querySelector(el);
        var text = str ? str : element.innerHTML;
        element.innerHTML = "";
        for (var i = 0; i < text.length; i++) {
          var letter = text[i];
          var span = document.createElement("span");
          var node = document.createTextNode(letter);
          var r = (360 / text.length) * i;
          var x = (Math.PI / text.length).toFixed(0) * i;
          var y = (Math.PI / text.length).toFixed(0) * i;
          span.appendChild(node);
          span.style.float = "left"
          span.style.webkitTransform =
            "rotateZ(" + r + "deg) translate3d(" + x + "px," + y + "px,0)";
          span.style.transform =
            "rotateZ(" + r + "deg) translate3d(" + x + "px," + y + "px,0)";
          element.appendChild(span);
        }
      }
    }
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
  [container] {
    background-color: #fff;
    border-radius: 20px;
    color: black;
  }
	[data-container] {
		padding: 0 1rem;
    margin: 1rem;
    background-color: #000;
    border: 1px solid white;
    border-radius: 20px;
    color: #fff;
	}
	[data-avatar]{
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
  }
  [textborder] {
    position: absolute;
    width: calc(100vw - 10px);
    height: calc(100vh -10px);
    padding: 5px;
    top: 50%;
    left: 50%;
    transform: translate3d(-50%,-50%,0) rotateZ(0);
    border-radius: 10px;
    /* animation: spinZ 20s linear infinite; */
    text-align: left;

    span {
      position: absolute;
      display: inline-block;
      left: 0;
      right: 0;
      top: 0;
      bottom: 0;
      text-transform: uppercase;
      font-family: courier, helvetica, arial, sans-serif;
      transition: all 0.5s cubic-bezier(0, 0, 0, 1);
      color: #000;
    }

    @keyframes spinZ {
      0% {
        transform: translate3d(-50%,-50%,0) rotateZ(360deg);
      }
      100% {
        transform:  translate3d(-50%,-50%,0) rotateZ(0deg);
      }
    }
	}
</style>
