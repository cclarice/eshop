<template>
  <div class="Eshop">
    <header class="EshopHeader">
      <h1>Добавление товара</h1>
      <BaseDropdown/>
    </header>
    <main class="EshopMain">
      <ProductForm class="EshopProductForm"
                   @addProduct="addProduct($event)"/>
      <ProductStack class="EshopProductStack"
                    :products="this.products"
                    @removeProduct="removeProduct($event)"/>
    </main>
  </div>
</template>

<script lang='js'>
import Vue from 'vue'
import BaseDropdown from "@/components/base/BaseDropdown";
import ProductForm from "@/components/eshop/ProductForm";
import ProductStack from "@/components/eshop/ProductStack";

export default Vue.extend({
  name: 'Eshop',
  components: { BaseDropdown, ProductForm, ProductStack },
  data () {
    return {
      products: [
        {
          id: 0,
          name: 'Fuel EX 2020',
          description: 'Двухподвес высшего уровня с оборудованием начального профессионального класса Sram, 12 скоростей',
          image: '/products/FuelEX2020.jpg',
          price: 257696
        },
        {
          id: 1,
          name: 'Marin Hawk Hill 1',
          description: 'Лучшее соотношение цены и качества, простая рекомендация для новичков и райдеров с ограниченным бюджетом',
          image: '/products/MarinHawkHill1.jpg',
          price: 133190
        },
        {
          id: 2,
          name: 'Maverick Juliana',
          description: 'Создан для прохождения самых разных трасс. Он маневренный и агрессивный. Райдеры могут регулировать геометрию с помощью флип-чипа',
          image: '/products/mavericJuliana.jpg',
          price: 348300
        },
        {
          id: 3,
          name: 'Image error',
          description: 'Image not found',
          price: 404
        }/*,
        {
          id: 3,
          name: 'Norco Aurum',
          description: 'Не важно, катаетесь вы в байк-парках или боретесь за секунды на гонках, Aurum готов к любым испытания вместе с вами',
          image: '/products/norcoAurum.jpg',
          price: 316630
        },
        {
          id: 4,
          name: 'HERO10 Black',
          description: 'Позволяет создавать видео 5.3K с удвоенной частотой кадров, фото 23 Мп, а также обеспечивает улучшенное качество',
          image: '/products/hero10black.jpeg',
          price: 49990
        },
        {
          id: 5,
          name: 'Helmet FOX v3',
          description: 'Самый технологичный мотошлем, который можно найти. Новая высокоэффективная система вентиляции и свежий подход к защите от прямых и боковых ударов.',
          image: '/products/foxHelmetv3.jpg',
          price: 16836
        }*/
      ]
    }
  },
  methods: {
    addProduct (product) {
      this.products.push(product)
    },
    removeProduct (productId) {
      this.products = this.products.filter(p => p.id !== productId)
    }
  }
})
</script>

<style scoped lang='scss'>
.Eshop {
  padding: 32px;
  .EshopHeader {
    width: 100%;
    height: 36px;

    display: flex;
    justify-content: space-between;

    h1 {
      font-weight: 600;
      font-size: 28px;
      line-height: 36px;
    }
  }
  .EshopMain {
    margin-top: 16px;
    width: 100%;
    height: auto;

    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    .EshopProductForm {
      width: calc(25% - 16px * 0.75);

      box-shadow: 0 20px 30px rgba(0, 0, 0, 0.04), 0 6px 10px rgba(0, 0, 0, 0.02);

      background-color: #FFFEFB;
      border-radius: 4px;
      padding: 24px;
    }
    .EshopProductStack {
      width: calc(75% - 16px * 0.25);
    }
  }
}

</style>