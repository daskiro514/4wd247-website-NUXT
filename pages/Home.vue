<template>
  <div id="home">
    <div class="sf-property--full-width">
      <SfHeader
        logo="/assets/logo.png"
        :logoHeight="75"
        :logoWidth="105"
        active-icon="account"
      >
        <template #navigation class="daskiro-navigation">
          <SfHeaderNavigationItem
            v-for="(category, key) in shopRootCategories"
            :key="`sf-header-navigation-item-${key}`"
            :link="`/${category}`"
            :label="category"
          />
        </template>
      </SfHeader>
      <SfHero>
        <SfHeroItem image="/assets/home-slider-image-1.jpg" />
        <SfHeroItem image="/assets/home-slider-image-2.jpg" />
        <SfHeroItem image="/assets/home-slider-image-3.jpg" />
      </SfHero>
      <div id="category">
        <div class="main section">
          <div class="products">
            <div class="product-filter">
              <h3 class="product-number">ALL (9)</h3>
              <div class="navbar__sort desktop-only">
                <SfComponentSelect v-model="sortBy" class="navbar__select">
                  <SfComponentSelectOption
                    v-for="option in sortByOptions"
                    :key="option.value"
                    :value="option.value"
                    class="sort-by__option"
                    >{{ option.label }}</SfComponentSelectOption
                  >
                </SfComponentSelect>
              </div>
            </div>
            <template>
              <div><hr class="sf-divider" /></div>
            </template>
            <transition-group
              v-if="isGridView"
              appear
              name="products__slide"
              tag="div"
              class="products__grid"
            >
              <SfProductCard
                v-for="(product, i) in products"
                :key="product.id"
                badgeLabel="Recommended"
                badgeColor="color-danger"
                :style="{ '--index': i }"
                :title="product.title"
                :image="product.image"
                :image-height="326"
                :image-width="216"
                :regular-price="product.price.regular"
                :special-price="product.price.special"
              />
            </transition-group>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import {
  SfHeader,
  SfImage,
  SfHero,
  SfProductCard,
  SfHeading,
  SfSidebar,
  SfButton,
  SfList,
  SfIcon,
  SfMenuItem,
  SfFilter,
  SfProductCardHorizontal,
  SfPagination,
  SfAccordion,
  SfComponentSelect,
  SfBreadcrumbs,
  SfColor,
  SfProperty,
  SfRadio,
  SfSelect,
} from "@storefront-ui/vue";
export default {
  name: "Home",
  components: {
    SfHeader,
    SfImage,
    SfHero,
    SfProductCard,
    SfHeading,
    SfButton,
    SfSidebar,
    SfIcon,
    SfList,
    SfFilter,
    SfProductCardHorizontal,
    SfPagination,
    SfMenuItem,
    SfAccordion,
    SfComponentSelect,
    SfBreadcrumbs,
    SfColor,
    SfProperty,
    SfRadio,
    SfSelect,
  },
  data() {
    return {
      shopRootCategories: ["SHOP BY", "ABOUT US", "EXPERTS", "CART (0)"],
      isGridView: true,
      sortBy: "",
      sortByOptions: [
        {
          value: "",
          label: "Filter By",
        },
        {
          value: "Date Added",
          label: "Date Added",
        },
        {
          value: "Recommended By",
          label: "Recommended By",
        },
        {
          value: "Price",
          label: "Price",
        },
      ],
      products: [
        {
          title: "GME UHF CB Radio XRS Connect Compact - XRS-390C",
          id: 1,
          description:
            "Find stunning women cocktail and party dresses. Stand out in lace and metallic cocktail dresses and party dresses from all your favorite brands.",
          image: "assets/product1.png",
          price: { regular: "$50", special: "$40" },
          rating: { max: 5, score: 5 },
          reviewsCount: 8,
          isInWishlist: true,
        },
        {
          title: "CTEK Battery Sense - 40-149",
          id: 2,
          description:
            "Find stunning women cocktail and party dresses. Stand out in lace and metallic cocktail dresses and party dresses from all your favorite brands.",
          image: "assets/product2.png",
          price: { regular: "$50", special: "$40" },
          rating: { max: 5, score: 4 },
          reviewsCount: 8,
          isInWishlist: false,
        },
        {
          title: "GME UHF CB Radio XRS Connect Compact - XRS-390C",
          id: 3,
          description:
            "Find stunning women cocktail and party dresses. Stand out in lace and metallic cocktail dresses and party dresses from all your favorite brands.",
          image: "assets/product3.png",
          price: { regular: "$50", special: "$40" },
          rating: { max: 5, score: 4 },
          reviewsCount: 8,
          isInWishlist: false,
        },
        {
          title: "CTEK Battery Sense - 40-149",
          id: 4,
          description:
            "Find stunning women cocktail and party dresses. Stand out in lace and metallic cocktail dresses and party dresses from all your favorite brands.",
          image: "assets/product1.png",
          price: { regular: "$50", special: "$40" },
          rating: { max: 5, score: 4 },
          reviewsCount: 8,
          isInWishlist: false,
        },
        {
          title: "GME UHF CB Radio XRS Connect Compact - XRS-390C",
          id: 5,
          description:
            "Find stunning women cocktail and party dresses. Stand out in lace and metallic cocktail dresses and party dresses from all your favorite brands.",
          image: "assets/product2.png",
          price: { regular: "$50", special: "$40" },
          rating: { max: 5, score: 4 },
          reviewsCount: 8,
          isInWishlist: false,
        },
        {
          title: "GME UHF CB Radio XRS Connect Compact - XRS-390C",
          id: 6,
          description:
            "Find stunning women cocktail and party dresses. Stand out in lace and metallic cocktail dresses and party dresses from all your favorite brands.",
          image: "assets/product3.png",
          price: { regular: "$50", special: "$40" },
          rating: { max: 5, score: 4 },
          reviewsCount: 8,
          isInWishlist: false,
        },
        {
          title: "GME UHF CB Radio XRS Connect Compact - XRS-390C",
          id: 7,
          description:
            "Find stunning women cocktail and party dresses. Stand out in lace and metallic cocktail dresses and party dresses from all your favorite brands.",
          image: "assets/product1.png",
          price: { regular: "$50", special: "$40" },
          rating: { max: 5, score: 4 },
          reviewsCount: 6,
          isInWishlist: false,
        },
        {
          title: "CTEK Battery Sense - 40-149",
          id: 8,
          description:
            "Find stunning women cocktail and party dresses. Stand out in lace and metallic cocktail dresses and party dresses from all your favorite brands.",
          image: "assets/product2.png",
          price: { regular: "$50", special: "$40" },
          rating: { max: 5, score: 4 },
          reviewsCount: 8,
          isInWishlist: false,
        },
        {
          title: "GME UHF CB Radio XRS Connect Compact - XRS-390C",
          id: 9,
          description:
            "Find stunning women cocktail and party dresses. Stand out in lace and metallic cocktail dresses and party dresses from all your favorite brands.",
          image: "assets/product2.png",
          price: { regular: "$50", special: "$40" },
          rating: { max: 5, score: 4 },
          reviewsCount: 8,
          isInWishlist: false,
        },
      ],
    };
  },
};
</script>

<style lang="scss">
@import "~@storefront-ui/vue/styles";
#home {
  .sf-link {
    font-family: Inter, sans-serif;
  }
  .product-number {
    font-family: Inter, sans-serif;
    color: rgb(77, 77, 77);
  }
  .sf-header__wrapper {
    background-color: #1a1a1a !important;
  }
  .sf-header__navigation {
    margin-right: 0px;
  }
  .sf-header__logo {
    margin: 0px;
  }
  .sf-header-navigation-item {
    width: 110px;
  }
  .sf-header-navigation-item__link {
    color: #bababa !important;
    font-size: 15px !important;
  }
  .sf-search-bar {
    display: none;
  }
  .sf-header__icons {
    display: none;
  }
  .sf-image {
    outline-color: transparent !important;
  }
  .sf-hero__control--left,
  .sf-hero__control--right {
    display: none;
  }
  .sf-hero__bullets .is-active {
    background-color: #bd0f16;
  }
  .products {
    margin: 30px;
  }
  .sf-product-card {
    background-color: #f9f9f9;
    margin-top: 20px;
    --product-card-max-width: 23rem;
    .sf-image {
      width: 100%;
    }
    .sf-product-card__badge {
      border-radius: 5px;
      font-size: 18px;
      font-weight: 600;
      margin: 0px;
      padding: 1px 10px;
      left: auto;
      right: 0px;
    }
    .sf-product-card__wishlist-icon {
      display: none;
    }
    .sf-product-card__add-button {
      display: block;
      position: absolute;
      opacity: 100;
      border-radius: 5px;
      height: 40px;
      bottom: -210px;
      left: 0px;
      width: 100%;
      background-color: #bd0f16;
    }
    .sf-product-card__add-button--icons::before {
      content: "shop now";
    }
    .color-white {
      display: none;
    }
    .sf-product-card__price {
      margin-bottom: 150px;
    }
    .sf-product-card__title {
      text-align: center;
      font-size: 22px;
      font-weight: 600;
      color: #333;
      white-space: inherit;
      line-height: 120%;
      text-transform: uppercase;
      margin-top: 0px;
      position: absolute;
    }
    .sf-product-card__price {
      // margin-top: 40px;
      font-family: sans-serif;
      position: relative;
      top: 100px;
    }
    .sf-price__regular {
      display: block;
      font-family: sans-serif;
      font-weight: 800;
      margin: -10px 0 0;
      left: 10px;
      color: #fff;
      font-size: 32px;
      text-align: center;
      text-shadow: 0 0 4px black, 0 0 8px black, 0 0 8px black, 0 0 9px black;
      position: relative;
    }
    .sf-price__regular::before {
      content: "RRP";
      margin: 0;
      font-size: 25px;
      color: #f3e123;
      text-align: center;
      font-weight: 900;
      text-shadow: 0 0 2px black, 0 0 4px black, 0 0 6px black, 0 0 8px black;
      display: block;
      line-height: 40%;
    }
    .sf-price__old {
      display: none;
    }
    .sf-price__special {
      font-weight: 900;
      margin: -20px 0 0;
      font-family: sans-serif;
      font-size: 48px;
      text-align: center;
      color: black;
      -webkit-text-fill-color: #f0e730;
      position: absolute;
      right: 10px;
      text-shadow: 0 0 12px black, 0 0 12px black;
      justify-content: center;
      align-items: center;
      display: block;
      line-height: 130%;
    }
    .sf-price__special::before {
      content: "NOW";
      margin: 0;
      font-size: 26px;
      color: #d9272a;
      text-align: center;
      font-weight: 900;
      outline: white;
      text-shadow: 0 0 2px black, 0 0 4px black, 0 0 6px black, 0 0 8px black;
      -webkit-text-stroke: 0.8px white;
      -webkit-text-fill-color: #d9272a;
      display: block;
      line-height: 10%;
    }
  }
  .product-filter{
    display: flex;
    justify-content: space-between;
    .sf-component-select {
      min-width: 200px;
    }
  }
}
#category {
  box-sizing: border-box;
  @include for-desktop {
    max-width: 1240px;
    margin: 0 auto;
  }
}
.main {
  &.section {
    padding: var(--spacer-xs);
    @include for-desktop {
      padding: 0;
    }
  }
}
.main {
  display: flex;
}
.products {
  box-sizing: border-box;
  flex: 1;
  margin: 0;
  &__grid,
  &__list {
    display: flex;
    flex-wrap: wrap;
  }
  &__grid {
    justify-content: center;
    @include for-desktop {
      justify-content: space-between;
    }
  }
}
</style>