<template>
  <div class="md-example-child md-example-child-tab-picker md-example-child-tab-picker-0">
              <md-field>
                <md-field-item
                  title="所在省市区"
                  arrow="arrow-right"
                  @click="province.show = !province.show"
                  placeholder="请选择"
                  :content="addressStr"
                  solid
                />
              </md-field>
              <md-tab-picker
                title="请选择"
                describe="请选择您所在的省份、城市、区县"
                large-radius
                :data="province.data"
                v-model="province.show"
                @change="handleChange"
              />
            </div>
</template>

<script>
import {Field, FieldItem, TabPicker} from 'mand-mobile'
import data from 'mand-mobile/components/tab-picker/demo/data'

export default {
  name: 'tab-bar-demo',
  /* DELETE */
  height: 550,
  /* DELETE */
  components: {
    [Field.name]: Field,
    [FieldItem.name]: FieldItem,
    [TabPicker.name]: TabPicker,
  },
  data() {
    return {
      province: {
          show: false,//是否出现选择器
          address: [],
          data: data,
        }
    }
  },
  computed: {
   addressStr() {
        return this.province.address.map(item => item.label).join(' ')
      },
  },
  methods: {
    handleChange({options}) {
        this.province.address = options
      },
  },
}

</script>
