<template>
        <section class="info_blurb">
            <div v-html="data.description"></div>
            <div v-html="data.cta"></div>
            <h2>HOURS</h2>
            <h4>Sunday	5PM–4AM<br>
            Monday	5PM–4AM<br>
            Tuesday	5PM–4AM<br>
            Wednesday	5PM–4AM<br>
            Thursday	5PM–4AM<br>
            Friday	5PM–6AM<br>
            Saturday	5PM–6AM</h4>
          <h2>CONTACT</h2>
          <ul>
                <li>
                    <p>
                        <a :href="`mailto:${data.contact.email}`">Email: {{ data.contact.email }}</a>
                    </p>
                </li>
                <li>
                    <p>
                        <a :href="`https://www.facebook.com/poorboysbar`">Facebook: poorboysbar</a>
                    </p>
                </li>
                <li>
                    <p>
                        <a :href="`https://www.instagram.com/poorboysbar/?hl=en`">Instagram: poorboysbar</a>
                    </p>
                </li>
            </ul>
        </section>
</template>

<script>
    export default {
        layout: 'layout',
        computed: {
            isInfoPage() {
                return this.$nuxt._route.name === "info" && true
            }
        },
        async asyncData() {
            try {
                const data = await import(`~/content/data/info.json`);
                return {
                data
                }
            } catch(err) {
                return false
            }
        },
        head() {
            return {
                bodyAttrs: {
                    style: this.isInfoPage && `background-color: ${this.data.background_color}; color: ${this.data.text_color}`
                }
            }
        }
    }
</script>

