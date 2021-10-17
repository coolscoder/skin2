<template>
  <div data-container>
    <img data-avatar :src="linkdrip.profile.image" />
    <h1 data-username v-text="linkdrip.profile.name.text"></h1>
    <p data-description v-text="linkdrip.profile.description.text"></p>
    <ul data-links>
      <li data-link-container v-for="(link, index) in linkdrip.links" v-bind:key="index">
        <LinkItem :link="link" />
      </li>
    </ul>
  </div>
</template>

<script>
  import LinkItem from './components/LinkItem.vue'

  export default {
    name: 'App',
    components: {
      LinkItem,
    },
    data: () => ({
      search: new URLSearchParams(window.location.search),
      visible: false,
      linktree: false,
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
        links: [
          {
            url: "http://google.com",
            label: "This is a link"
          },
          {
            url: "http://google.com",
            label: "This is a link"
          },
          {
            url: "http://google.com",
            label: "This is a link"
          },
          {
            url: "http://google.com",
            label: "This is a link"
          }
        ]
      }
    })
  }
</script>

<style lang="scss">
  body{
    background: #000;
    color: #fff;
    font-family: Helvetica;
    text-align: center;
  }
	[data-container] {
		margin: 0 auto;
		max-width: 30rem;
		padding: 0 1rem;
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
		margin: 2rem 0 2rem;
		li{
			margin: 0 0 1rem 0;
      padding: 1rem 1.25rem;
      border: 1px solid #fff; 
      display: flex;
      justify-content: center;
      cursor: pointer;
			a {
				display: block;
				font-size: 1rem;
				position: relative;
				color: inherit;
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
</style>
