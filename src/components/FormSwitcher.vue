<template lang="pug">
    .form-switcher
        weapon-form
</template>

<script lang="ts">
import {Component, Prop, Vue} from 'vue-property-decorator';
import WeaponForm from "@/components/WeaponForm.vue";

@Component({
    components: {
        'weapon-form': WeaponForm
    }
})
export default class FormSwitcher extends Vue {
    @Prop() private msg!: string;
}
</script>

<style scoped lang="less">
</style>
