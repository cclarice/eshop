<template>
  <div class="Eshop">
    <header class="EshopHeader">
      <h1>Добавление товара</h1>
      <BaseDropdown class="EshopDropdown"
                    :options="sortOptions"
                    :default="sortOptions[0]"
                    @changeValue="sort($event)"/>
    </header>
    <main class="EshopMain">
      <ProductForm class="EshopProductForm"
                   @addProduct="addProduct($event)"/>
      <ProductStack v-if="!sorting"
                    class="EshopProductStack"
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
        },
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
        }
      ],
      sortOptions: [
        {
          name: '',
          text: 'По умолчанию'
        },
        {
          name: 'byName',
          text: 'По Имени'
        },
        {
          name: 'byPriceMax',
          text: 'Цена: 📈'
        },
        {
          name: 'byPriceMin',
          text: 'Цена: 📉'
        }
      ],
      sorting: false
    }
  },
  methods: {
    addProduct (product) {
      this.products.push(product)
    },
    removeProduct (productId) {
      this.products = this.products.filter(p => p.id !== productId)
    },
    async sort (sortOption) {
      const pro = this.products
      this.sorting = true

      function sortSort (his) {
        if (sortOption === '') {
          his.products = pro.sort((firstEl, secondEl) => { return firstEl.id > secondEl.id ? 1 : -1 })
        } else if (sortOption === 'byName') {
          his.products = pro.sort((firstEl, secondEl) => { return firstEl.name > secondEl.name ? 1 : -1 })
        } else if (sortOption === 'byPriceMax') {
          his.products = pro.sort((firstEl, secondEl) => { return firstEl.price > secondEl.price ? 1 : -1 })
        } else if (sortOption === 'byPriceMin') {
          his.products = pro.sort((firstEl, secondEl) => { return firstEl.price < secondEl.price ? 1 : -1 })
        }
        his.sorting = false
      }

      setTimeout(sortSort, 100, this)
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
    justify-content: flex-end;

    h1 {
      position: absolute;
      width: calc(100% - 64px);
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
      width: calc(20% - 16px * 0.8);

      box-shadow: 0 20px 30px rgba(0, 0, 0, 0.04), 0 6px 10px rgba(0, 0, 0, 0.02);

      background-color: #FFFEFB;
      border-radius: 4px;
      padding: 24px;
    }
    .EshopProductStack {
      width: calc(80% - 16px * 0.2);
    }
  }
}

@media (min-width: 1984px) {
  .Eshop {
    padding: 32px calc((100vw - 1920px) / 2);
    h1 {
      width: calc(100vw - (100vw - 1920px)) !important;
    }
  }
}

@media (max-width: 1692px) {
  .Eshop {
    .EshopMain {
      margin-top: 16px;
      width: 100%;
      height: auto;
      .EshopProductForm {
        width: calc(25% - 16px * 0.75);
      }
      .EshopProductStack {
        width: calc(75% - 16px * 0.25);
      }
    }
  }
}

@media (max-width: 1360px) {
  .Eshop {
    .EshopMain {
      margin-top: 16px;
      width: 100%;
      height: auto;
      .EshopProductForm {
        width: calc(33.3333% - 16px * 0.6666);
      }
      .EshopProductStack {
        width: calc(66.6666% - 16px * 0.3333);
      }
    }
  }
}

@media (max-width: 1028px) {
  .Eshop {
    .EshopMain {
      margin-top: 16px;
      width: 100%;
      height: auto;
      .EshopProductForm {
        width: calc(50% - 16px * 0.5);
      }
      .EshopProductStack {
        width: calc(50% - 16px * 0.5);
      }
    }
  }
}

@media (max-width: 696px) {
  .Eshop {
    h1 {
      font-size: 20px !important;
    }
    .EshopMain {
      margin-top: 16px;
      width: 100%;
      height: auto;
      display: flex;
      flex-wrap: wrap;
      .EshopProductForm {
        width: 100%;
      }
      .EshopProductStack {
        padding-top: 16px;
        width: 100%;
      }
    }
  }
}
</style>