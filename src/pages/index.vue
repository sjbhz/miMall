<template>
  <div class="index">
    <div class="container">
      <div class="swiper-box">
        <div class="nav-menu">
          <ul class="menu-wrap">
            <li class="menu-item">
              <a href="javascript:;">手机 电话卡</a>
              <div class="children">
                <ul v-for="(item,index) in menuList" v-bind:key="index">
                  <li v-for="(sub, subIndex) in item " v-bind:key="subIndex">
                    <a v-bind:href="sub?'/#/product/'+sub.id:''">
                      <img v-bind:src="sub&&sub.img || '/imgs/item-box-1.png'" alt />
                      {{sub&&sub.name || "小米9"}}
                    </a>
                  </li>
                </ul>
              </div>
            </li>
            <li class="menu-item">
              <a href="javascript:;">电视 盒子</a>
            </li>
            <li class="menu-item">
              <a href="javascript:;">笔记本 平板</a>
            </li>
            <li class="menu-item">
              <a href="javascript:;">家电 插线板</a>
            </li>
            <li class="menu-item">
              <a href="javascript:;">出行 穿戴</a>
            </li>
            <li class="menu-item">
              <a href="javascript:;">智能 路由器</a>
            </li>
            <li class="menu-item">
              <a href="javascript:;">电源 配件</a>
            </li>
            <li class="menu-item">
              <a href="javascript:;">生活 箱包</a>
            </li>
          </ul>
        </div>
        <div class="swiper-container">
          <div class="swiper-wrapper">
            <div class="swiper-slide">
              <a v-bind:href="'/#/product/42'">
                <img v-bind:src="'/imgs/slide-1.jpg'" alt />
              </a>
            </div>
          </div>
        </div>
        <div class="ads-box">
          <a href v-for="(item,index) in adsList" v-bind:key="index">
            <!-- <img v-bind:src="item.img" /> -->
            <img v-lazy="item.img" />
          </a>
        </div>
        <div class="banner">
          <a href>
            <!-- <img src="/imgs/banner-1.png" /> -->
            <img v-lazy="'/imgs/banner-1.png'" />
          </a>
        </div>
        <div class="product-box">
          <div class="container">
            <h2>手机</h2>
            <div class="wrapper">
              <div class="banner-left">
                <a href="/#/product/35">
                  <!-- <img src="/imgs/mix-alpha.jpg" /> -->
                  <img v-lazy="'/imgs/mix-alpha.jpg'" />
                </a>
              </div>
              <div class="list-box">
                <div class="list" v-for="(item,index) in phoneList" v-bind:key="index">
                  <div class="item" v-for="(sub,subindex) in item" v-bind:key="subindex">
                    <span v-bind:class="{'new-pro':subindex%2==0}">新品</span>
                    <div class="item-img">
                      <img
                        src="https://cdn.cnbj1.fds.api.mi-img.com/mi-mall/6f2493e6c6fe8e2485c407e5d75e3651.jpg"
                        alt
                      />
                    </div>
                    <div class="item-info">
                      <h3>小米9</h3>
                      <p>骁龙855,索尼4800万超广角微距</p>
                      <p class="price" @click="addCart">2999元</p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <ServiceBar></ServiceBar>
    <Modal
      title="提示"
      sureText="查看购物车"
      btnType="1"
      modalType="middle"
      :showModal="showModal"
      v-on:submit="goToCart"
      v-on:cancel="showModal=false"
    >
      <template v-slot:body>
        <p>商品添加成功</p>
      </template>
    </Modal>
  </div>
</template>

<script>
import ServiceBar from "./../components/ServiceBar";
import Modal from "./../components/Modal";
export default {
  name: "index",
  components: {
    ServiceBar,
    Modal
  },
  data() {
    return {
      swiperOption: {
        autoplay: true,
        loop: true,
        effect: "cube"
      },
      slideListOne: [
        {
          id: "42",
          img: "/imgs/slide-1.jpg"
        }
      ],
      slideList: [
        {
          id: "42",
          img: "/imgs/slide-1.jpg"
        },
        {
          id: "45",
          img: "/imgs/slide-2.jpg"
        },
        {
          id: "46",
          img: "/imgs/slide-3.jpg"
        },
        {
          id: " ",
          img: "/imgs/slide-4.jpg"
        },
        {
          id: " ",
          img: "/imgs/slide-5.jpg"
        }
      ],
      menuList: [
        [
          {
            id: 30,
            img: "/imgs/item-box-1.png",
            name: "小米CC9"
          },
          {
            id: 31,
            img: "/imgs/item-box-2.png",
            name: "小米8青春版"
          },
          {
            id: 32,
            img: "/imgs/item-box-1.png",
            name: "Redmi K20 Pro"
          },
          {
            id: 33,
            img: "/imgs/item-box-1.png",
            name: "移动4G专区"
          }
        ],
        [0, 0, 0, 0],
        [0, 0, 0, 0],
        [0, 0, 0, 0],
        [0, 0, 0, 0],
        [0, 0, 0, 0]
      ],
      adsList: [
        {
          id: 33,
          img: "/imgs/ads-1.png"
        },
        {
          id: 48,
          img: "/imgs/ads-2.jpg"
        },
        {
          id: 45,
          img: "/imgs/ads-3.png"
        },
        {
          id: 47,
          img: "/imgs/ads-4.jpg"
        }
      ],
      phoneList: [
        [1, 1, 1, 1],
        [1, 1, 1, 1]
      ],
      showModal: false
    };
  },
  created() {},
  mounted() {},
  methods: {
    // showModal() {}
    addCart() {
      this.showModal = true;
      return;
      // this.axios
      //   .post("/carts", {
      //     productId: id,
      //     selected: true
      //   })
      //   .then(() => {})
      //   .catch(() => {
      //     this.showModal = true;
      //   });
    },
    goToCart() {
      this.$router.push("/cart");
    }
  }
};
</script>
<style lang="scss">
@import "./../assets/scss/config.scss";
@import "./../assets/scss/mixin.scss";
.index {
  .swiper-box {
    .nav-menu {
      position: absolute;
      width: 264px;
      height: 461px;
      z-index: 9;
      padding: 26px 0;
      background: #55585a7a;
      box-sizing: border-box;
      .menu-wrap {
        .menu-item {
          height: 50px;
          line-height: 50px;
          a {
            position: relative;
            display: block;
            font-size: 16px;
            color: #fff;
            padding-left: 30px;
            &:after {
              position: absolute;
              right: 30px;
              top: 17.5px;
              content: "";
              @include bgImg(10px, 15px, "/imgs/icon-arrow.png");
            }
          }
          &:hover {
            background: $colorA;
            .children {
              display: block;
            }
          }
          .children {
            display: none;
            width: 962px;
            height: 451px;
            background: $colorG;
            position: absolute;
            top: 0;
            left: 264px;
            border: 1px solid $colorH;
            ul {
              display: flex;
              justify-content: space-between;
              height: 75px;
              li {
                height: 75px;
                line-height: 75px;
                width: 241px;
                padding-left: 23px;
              }
              a {
                color: $colorB;
                font-size: 14px;
              }
              img {
                width: 42px;
                height: 35px;
                vertical-align: middle;
                margin-right: 15px;
              }
            }
          }
        }
      }
    }
    .swiper-container {
      height: 451px;
      img {
        width: 100%;
        height: 100%;
      }
    }
    .ads-box {
      // @include flex();
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-top: 14px;
      margin-bottom: 31px;
      a {
        width: 296px;
        height: 167px;
      }
    }
    .banner {
      margin-bottom: 50px;
    }
    .product-box {
      background: $colorJ;
      padding: 30px 0 50px;
      h2 {
        font-size: $fontF;
        height: 21px;
        line-height: 21px;
        color: $colorB;
        margin-bottom: 20px;
      }
      .wrapper {
        display: flex;
        .banner-left {
          margin-right: 16px;
          img {
            width: 224px;
            height: 619px;
          }
        }
        .list-box {
          .list {
            @include flex();
            width: 986px;
            margin-bottom: 14px;
            &:last-child {
              margin-bottom: 0;
            }
            .item {
              width: 236px;
              height: 302px;
              background: $colorG;
              text-align: center;
              span {
                display: inline-block;
                width: 67px;
                height: 24px;
                font-size: 14px;
                line-height: 24px;
                color: $colorG;
                &.new-pro {
                  background: #7ecf68;
                }
                &.kill-pro {
                  background: #e82626;
                }
              }
              .item-img {
                img {
                  height: 195px;
                }
              }
              .item-info {
                h3 {
                  font-size: $fontJ;
                  color: $colorB;
                  line-height: $fontJ;
                  font-weight: bold;
                }
                p {
                  color: $colorD;
                  line-height: 13px;
                  margin: 6px auto 13px;
                }
                .price {
                  color: #f20a02;
                  font-size: $fontJ;
                  font-weight: bold;
                  cursor: pointer;
                  &:after {
                    @include bgImg(22px, 22px, "/imgs/icon-cart-hover.png");
                    content: "";
                    margin-left: 5px;
                    vertical-align: middle;
                  }
                }
              }
            }
          }
        }
      }
    }
  }
}
</style>
