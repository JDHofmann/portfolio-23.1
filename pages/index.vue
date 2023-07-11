<template>
    <div>
        <header>
            <NuxtLink
				class="home-link"
				to="/"
				title="homepage"
			>
				<!-- <img
					class="logo"
					src="inclusity-logo.svg"
					alt="Inclusity logo"
				/> -->
                <span>JDBH</span>
			</NuxtLink>
            <nav
				:class="
					menuIsActive
						? 'showing-menu-content'
						: 'hiding-menu-content'
				"
			>
				<button
					:aria-haspopup="menuIsActive ? 'true' : 'false'"
					:aria-expanded="menuIsActive ? 'false' : 'true'"
					data-toggle="dropdown"
					class="mobile-menu-btn"
					@click="toggleMenu"
				>
					<span></span>
					<span></span>
					<span></span>
				</button>
                <ul>
                    <li>one</li>
                    <li>two</li>
					<!-- <li
						class="menu-section-item"
						v-for="(s, i) in navigation"
						:key="i"
					> -->
						<!-- {{ s.title }} -->
						<!-- <MenuItemES
							@toggleSubMenuItem="subMenuActiveItemUpdate"
							:isActive="subMenuActiveItem === s.name"
							:name="s.name"
							:title="s.title"
							:color="s.color"
							role="menu"
						>
							<li v-for="(l, j) in s.links" :key="j">
								<a :href="l.url">{{ l.text }}</a>
								<a v-if="l.es" :href="l.es.url">{{
									l.es.text
								}}</a>
							</li>
						</MenuItemES> -->
					<!-- </li> -->
				</ul>
            </nav>
        </header>
        <h1>Index</h1>
    </div>
</template>
<script>
export default {
	layout: 'empty',
	data() {
		return {
			menuIsActive: false,
        }
    },
    methods: {
		toggleMenu() {
			this.menuIsActive
				? ((this.subMenuActiveItem = null), (this.menuIsActive = false))
				: (this.menuIsActive = true)
		},

	},
}

</script>

<style lang="scss" scoped>
$x-gutter: clamp(10px, (5px + 2.5vw), 40px);
$y-gutter: clamp(10px, calc(10px + 1vw), 20px);
header {
	// background: #ffffff;
	padding: $y-gutter $x-gutter;
	position: relative;
	top: 0;
	.home-link {
		display: inline-block;
		.logo {
			height: 45px;
		}
	}
}
nav {
	.mobile-menu-btn {
		$line-height: 1px;
		// background: #ffffff;
		border: 1px solid #ff00ff;
		border-radius: 8px;
		height: 40px;
		left: auto;
		padding: 0.43rem;
		position: absolute;
		right: $x-gutter;
		top: $y-gutter;
		transition: 0.5s ease;
		width: 40px;
		span {
			background: #ff00ff;
			display: block;
			height: $line-height;
			line-height: 0px;
			position: absolute;
			top: 50%;
			transition: 0.5s ease;
			width: 25px;
			&:nth-child(1) {
				transform: translateY(-8px);
			}
			&:nth-child(3) {
				transform: translateY(8px);
			}
		}
	}
	ul {
		display: none;
		padding-top: $y-gutter;
		right: $x-gutter;
        li {
            color: #00ffff;
        }
	}
    &.showing-menu-content {
		.mobile-menu-btn {
			span {
				&:nth-child(1) {
					transform: rotate(45deg) translate(0);
				}
				&:nth-child(2) {
					opacity: 0;
				}
				&:nth-child(3) {
					transform: rotate(-45deg) translate(0);
				}
			}
		}
	}
	.navigation-dropdown-content {
		display: none;
	}
}
nav.showing-menu-content {
	ul {
		display: block;
	}
}
</style>