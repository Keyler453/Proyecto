<script setup>
import SidebarLink from '@/Components/SidebarLink.vue';
import Welcome from '@/Pages/Welcome.vue';
defineProps({
	canRegister: {
		type: Boolean,
	},
});

const emit = defineEmits(['openModal']);
</script>

<template>
	<div class="fixed top-0 left-0 z-40 w-55 h-screen hidden sm:block bg-white border-0 pt-20 min-h-screen px-2">
		<!-- Primary Sidebar Menu -->
		<div class="w-full h-full mx-auto flex flex-col justify-between">
			<!-- Navigation Links -->
			<div class="flex flex-col gap-y-1">
				<SidebarLink :href="route('home')" :active=" route().current( 'incio' )">
					  <div class="icon-text">
						<font-awesome-icon :icon="['fas', 'house']" />
						Inicio
					</div>
				</SidebarLink>
				<SidebarLink :href=" route( 'divulgation' )" :active=" route().current( 'divulgation' ) ">
					<div class="icon-text">
						<font-awesome-icon :icon="['fas', 'message']" />
					Divulgación
				</div>
				</SidebarLink>
				<SidebarLink :href=" route( 'convocations.index' ) " :active=" route().current( 'convocations.index' ) ">
					<div>
						<font-awesome-icon :icon="['fas', 'file']" />
					Convocatorias
				</div>
				</SidebarLink>
				<SidebarLink :href=" route( 'gallery' ) " :active=" route().current( 'gallery' ) ">
					<div class="icon-text">
						<font-awesome-icon :icon="['fas', 'images']" />
					Galería
				</div>
				</SidebarLink>
				<SidebarLink :href=" route( 'reime' ) " :active=" route().current( 'reime' ) ">
					<div class="icon-text">
						<font-awesome-icon :icon="['fas', 'comment']" />
						REIME	
					</div>
				</SidebarLink>
				<SidebarLink :href=" route( 'contact' ) " :active=" route().current( 'contact' ) ">
					<div class="icon-text">
						<font-awesome-icon :icon="['fas', 'address-book']" />
						Contacto
					</div>
				</SidebarLink>
			</div>

			<!-- Register button-->
			<div class="flex justify-center items-center pb-8">
				<Link v-if=" $page.props.auth.user.name " :href=" route( 'reime' ) "
					class="px-8 py-2 rounded-full bg-neutral-200 text-sky-500 hover:bg-sky-500 hover:text-white font-bold transition-all duration-200">
				Página principal REIME
				</Link>
				
				<!-- <Link v-else :href=" route( 'register' ) "
					class="px-8 py-2 rounded-full bg-neutral-200 text-sky-500 hover:bg-sky-500 hover:text-white font-bold transition-all duration-200">
				Únete a la REIME
				</Link> -->

				<span v-else @click="emit('openModal', 'register')" class="px-8 py-2 rounded-full bg-neutral-200 text-sky-500 hover:bg-sky-500 hover:text-white font-bold transition-all duration-200">
					Únete a la REIME
				</span>
			</div>
		</div>
	</div>
</template>
