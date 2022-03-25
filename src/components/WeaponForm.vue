<template lang="pug">
    .weapon_form
        form
            table
                colgroup
                    col(style="width: 100px;")
                    col(style="width: 300px;")
                tr
                    th 名称
                    td
                        input(type="text" :value="item.name")
                tr
                    th 種別
                    td
                        input(type="text" :value="item.type")
                        assist-button(name="equip_part" items="片手剣,両手剣,斧" @value-changed="value_changed")
                tr
                    th レベル
                    td
                        input(type="text" :value="item.level")
                tr
                    th 重量
                    td
                        input(type="text" :value="item.weight")
                tr
                    th 命中補正
                    td
                        input(type="text" :value="item.hit_adjust")
                tr
                    th  攻撃力
                    td
                        input(type="text" :value="item.attack")
                tr
                    th 行動修正
                    td
                        input(type="text" :value="item.initiative_adjust")
                tr
                    th  射程
                    td
                        input(type="text" :value="item.range")
                tr
                    th  装備部位
                    td
                        input(type="text" :value="item.equip_part")
                        assist-button(name="equip_part" items="頭,体,片手,両手,装身具" @value-changed="value_changed")
                tr
                    th  価格
                    td
                        input(type="text" :value="item.price")
                tr
                    th  鑑定値
                    td
                        input(type="text" :value="item.appraisal")
                tr
                    th  効果
                    td
                        textarea(:value="item.text")
                tr
                    th  解説
                    td
                        textarea(:value="item.description")

</template>

<script lang="ts">
import {Component, Prop, Vue} from 'vue-property-decorator';
import {SourceWeapon, RawSourceWeapon} from "@/types";
import AssistButton from "@/components/AssistButtons.vue";

@Component({
    components: {'assist-button': AssistButton}
})
export default class WeaponForm extends Vue {
    item: SourceWeapon = {
        template: 'weapon',
        name: '',
        type: '',
        level: '1',
        weight: '',
        hit_adjust: '', // 命中修正：-1
        attack: '', // 攻撃力：+[CL+7]
        initiative_adjust: '', // 行動修正：-1
        range: '', // 射程：至近
        equip_part: '', // 装備部位：片
        price: '', // 価格：12000
        appraisal: '', // 鑑定値：16
        text: '', // 効果：パッシブ。この武器を使用した白兵攻撃のダメージに+2Dする。
        description: ''// 解説：
    }

    value_change(key: keyof RawSourceWeapon, value: string): void {
        this.item[key] = value;
    }

    value_changed(info: { key: keyof RawSourceWeapon, value: string }) {
        this.value_change(info.key, info.value);
    }

}
</script>

<style scoped lang="less">
</style>
