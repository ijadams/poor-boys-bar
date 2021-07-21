<template>
    <section>
        <ul class="list">
            <NuxtLink
                v-for="post in sortedPosts"
                :key="post.attributes.title"
                :to="`/blog/${formatSlug(post.attributes.title)}`"
            >
                <li>
                    <div class="hero_image">
                      <v-img
                          lazy-src="https://res.cloudinary.com/ia-interactive/image/upload/v1626901063/18921857_675715349281682_2494108169411996645_n_v1xjky.jpg"
                          :alt="post.attributes.title"
                          height="100%"
                          width="100%"
                          :src="post.attributes.hero_image"
                      ></v-img>
                    </div>
                    <div class="blogList__info">
                        <h2>{{ post.attributes.title }}</h2>
                        <h3>{{ formatDate(post.attributes.date) }}</h3>
                    </div>
                </li>
            </NuxtLink>
        </ul>
    </section>
</template>
<script>
    export default {
        props: {
            posts: {
                type: Array,
                required: true
            }
        },
        computed: {
            sortedPosts() {
                const sortedPosts = this.posts
                sortedPosts.sort((a,b) => {
                    const dateA = new Date(a.attributes.date);
                    const dateB = new Date(b.attributes.date);
                    if (dateA < dateB) {
                        return 1;
                    }
                    if (dateA > dateB) {
                        return -1;
                    }
                    return 0;
                })
                return sortedPosts
            }
        },
        methods: {
            formatDate(date) {
                return new Date(date).toDateString().slice(4)
            },
            formatExcerpt(body) {
                return body.slice(0 , 200).trimEnd()
            },
            formatSlug(title) {
                const regex = / /gi;
                return title.toLowerCase().trim().replace(regex, "-")
            }
        }
    }
</script>

/*
TODO -- i would love to figure out how to show the md in the summary...
right now its just plaintext not sure how to target the loader to parse this
 */
