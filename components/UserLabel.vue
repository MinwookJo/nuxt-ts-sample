<template>
  <div>
      FName: {{user.firstName}}
      LName: {{user.lastName}}
      {{fullName}}
      {{message}}
  </div>
</template>

<script lang="ts">
import Vue, {PropOptions} from 'vue';

interface User {
    firstName: string,
    lastName: string
}

export default Vue.extend ({
    name: 'UserLabel',
    props: {
        user: {
            type: Object,
            required: true
        } as PropOptions<User>
    },
    data() {
        return {
            message: 'this is local state'
        }
    },

    computed: {
        fullName(): string {
            return `${this.user.firstName} ${this.user.lastName}`;
        }
    }
})
</script>

<style>

</style>