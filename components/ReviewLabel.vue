<template>
    <div @click="click">
      Title: {{review.title}}
      Content: {{review.content}}
      fullReview: {{getterFullReview}}
      score: {{score}}
      message: {{message}}
  </div>
</template>

<script lang="ts">
import { Prop, Watch, Emit, Component, Vue } from 'vue-property-decorator';

interface Review {
    title: string,
    content: string
}
@Component
export default class ReviewLabel extends Vue {
    // props
    @Prop({default: {title: '', content: ''}, required: true}) 
    readonly review!: Review;
    @Prop({type: Number, default: 0, required: true}) 
    readonly score!: number;

    // local state
    message: string = 'this is local state'
    
    // computed
    get getterFullReview(): string {
        return this.review.title + this.review.content;
    }
    // watch
    @Watch('score', {immediate: true, deep: false})
    printScore(value: number, oldValue: number): void {
        console.log('old', oldValue);
        console.log('new', value);
    }

    @Emit()
    click(e: Event): Event {
        console.log(e)
        return e
    }
}
</script>

<style scoped>

</style>

