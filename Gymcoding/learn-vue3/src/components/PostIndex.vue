<template>
	<main>
		<div class="container py-4">
			<PostCreate @create-post="createPost"></PostCreate>
			<hr class="my-4" />
			<div class="row g-4">
				<div v-for="post in posts" :key="post.id" class="col col-4">
					<PostItem
						:title="post.title"
						:contents="post.contents"
						:type="post.type"
						:is-like="post.isLike"
						@toggle-like="toggleLike(post)"
					></PostItem>
				</div>
			</div>
			<hr class="my-4" />
			<LabelInput
				v-model="username"
				label="이름"
				class="parent-class"
				style="color: red"
				id="parent-id"
			></LabelInput>
		</div>
	</main>
</template>

<script>
import PostItem from './PostItem.vue';
import PostCreate from './PostCreate.vue';
import LabelInput from './LabeInput.vue';
import { reactive, ref } from 'vue';
export default {
	components: {
		PostItem,
		PostCreate,
		LabelInput,
	},
	setup() {
		const obj = reactive({
			title: '제목2',
			contents: '내용2',
		});
		const posts = reactive([
			{ id: 1, title: '제목1', contents: '내용1', isLike: true, type: 'news' },
			{ id: 2, title: '제목2', contents: '내용2', isLike: true, type: 'news' },
			{ id: 3, title: '제목3', contents: '내용3', isLike: true, type: 'news' },
			{
				id: 4,
				title: '제목4',
				contents: '내용4',
				isLike: false,
				type: 'notice',
			},
			{ id: 5, title: '제목5', contents: '내용5', isLike: false, type: 'news' },
		]);
		const createPost = newPost => {
			console.log('newPost: ', newPost);
			posts.push(newPost);
		};
		const username = ref('');
		const firstname = ref('');
		const lastname = ref('');
		return { obj, posts, createPost, username, firstname, lastname };
	},
};
</script>

<style></style>
