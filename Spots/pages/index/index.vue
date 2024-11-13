<template>
  <view class="container">
    <view class="search-bar">
      <input type="text" placeholder="搜索省份" v-model="searchQuery" />
    </view>
    <view class="province-grid">
      <view class="province-item" v-for="province in filteredProvinces" :key="province.name">
        <view class="province-card">
          <image :src="province.image" class="province-image" />
          <view class="province-info">
            <text class="province-name">{{ province.name }}</text>
            <checkbox class="province-checkbox" :value="province.name" v-model="selectedProvinces"></checkbox>
          </view>
        </view>
      </view>
    </view>
    <button class="province-next-button" @click="nextStep">下一步</button>
  </view>
</template>

<script>
import Beijing from '@/static/Beijing.png';
import Shanghai from '@/static/Shanghai.png';
import Tianjin from '@/static/Tianjin.png';
import Chongqing from '@/static/Chongqing.png';
import Hebei from '@/static/Hebei.png';
import Shanxi from '@/static/Shanxi.png';
import Neimenggu from '@/static/Neimenggu.png';
import Liaoning from '@/static/Liaoning.png';
import Jilin from '@/static/Jilin.png';
import Heilongjiang from '@/static/Heilongjiang.png';
import Jiangsu from '@/static/Jiangsu.png';
import Zhejiang from '@/static/Zhejiang.png';
import Anhui from '@/static/Anhui.png';
import Fujian from '@/static/Fujian.png';
import Jiangxi from '@/static/Jiangxi.png';
import Shandong from '@/static/Shandong.png';
import Henan from '@/static/Henan.png';
import Hubei from '@/static/Hubei.png';
import Hunan from '@/static/Hunan.png';
import Guangdong from '@/static/Guangdong.png';
import Guangxi from '@/static/Guangxi.png';
import Hainan from '@/static/Hainan.png';
import Sichuan from '@/static/Sichuan.png';
import Guizhou from '@/static/Guizhou.png';
import Yunnan from '@/static/Yunnan.png';
import Xizang from '@/static/Xizang.png';
import Shaanxi from '@/static/Shaanxi.png';
import Gansu from '@/static/Gansu.png';
import Qinghai from '@/static/Qinghai.png';
import Ningxia from '@/static/Ningxia.png';
import Xinjiang from '@/static/Xinjiang.png';
import Hongkong from '@/static/Hongkong.png';
import Macau from '@/static/Macau.png';
import Taiwan from '@/static/Taiwan.png';

export default {
  data() {
    return {
      searchQuery: '',
      selectedProvinces: [],
      provinces: [
        { name: '北京', image: Beijing },
        { name: '上海', image: Shanghai },
        { name: '天津', image: Tianjin },
        { name: '重庆', image: Chongqing },
        { name: '河北', image: Hebei },
        { name: '山西', image: Shanxi },
        { name: '内蒙古', image: Neimenggu },
        { name: '辽宁', image: Liaoning },
        { name: '吉林', image: Jilin },
        { name: '黑龙江', image: Heilongjiang },
        { name: '江苏', image: Jiangsu },
        { name: '浙江', image: Zhejiang },
        { name: '安徽', image: Anhui },
        { name: '福建', image: Fujian },
        { name: '江西', image: Jiangxi },
        { name: '山东', image: Shandong },
        { name: '河南', image: Henan },
        { name: '湖北', image: Hubei },
        { name: '湖南', image: Hunan },
        { name: '广东', image: Guangdong },
        { name: '广西', image: Guangxi },
        { name: '海南', image: Hainan },
        { name: '四川', image: Sichuan },
        { name: '贵州', image: Guizhou },
        { name: '云南', image: Yunnan },
        { name: '西藏', image: Xizang },
        { name: '陕西', image: Shaanxi },
        { name: '甘肃', image: Gansu },
        { name: '青海', image: Qinghai },
        { name: '宁夏', image: Ningxia },
        { name: '新疆', image: Xinjiang },
        { name: '香港', image: Hongkong },
        { name: '澳门', image: Macau },
        { name: '台湾', image: Taiwan },
      ],
    };
  },
  computed: {
    filteredProvinces() {
      return this.provinces.filter(province => province.name.includes(this.searchQuery));
    },
  },
  methods: {
    nextStep() {
      // 处理下一步逻辑
      console.log(this.selectedProvinces);
    },
  },
};
</script>

<style>
.container {
  padding: 20px;
}
.search-bar {
  margin-bottom: 20px;
}
.province-grid {
  display: flex;
  flex-wrap: wrap;
}
.province-item {
  width: 28%; /* 每行三个省份 */
  margin: 2%;
  text-align: center;
}
.province-card {
  border: 3px solid #ccc;
  border-radius: 30px 30px 0px 30px;
  position: relative;
  overflow: hidden;
  background-color: white;
}
.province-card::before {
  content: '';
  position: absolute;
  top: -10px;
  left: 50%;
  transform: translateX(-50%);
  width: 0;
  height: 0;
  border-left: 10px solid transparent;
  border-right: 10px solid transparent;
  border-bottom: 10px solid white;
}
.province-image {
  width: 100%;
  height: 160px;
}
.province-info {
  display: flex;
  justify-content: space-between;
  align-items: left;
  gap: 5px;  /* 控制名字和复选框之间的间距 */
  margin: 10px 2px;
}

.province-name {
	font-size: 28px;
	font-weight: 600;
	color: #333;
    font-weight: bold;
    margin-right: 88px;
    margin-bottom: 10px;/* 移除原有的margin */
    flex: 1;    /* 让文字占据剩余空间 */
    white-space: nowrap; /* 防止文字换行 */
    overflow: hidden; /* 超出部分隐藏 */
    text-overflow: ellipsis; /* 超出显示省略号 */
}

.province-checkbox {
    transform: scale(1.5);
    margin-right: 40px;
    margin-top: 10px;  /* 移除原有的margin */
    margin-right: 10px; /* 减小右边距 */
    margin-top: 10px;
    flex-shrink: 0; /* 防止复选框被压缩 */
}
.province-next-button {
  width: 80%;
  height: 80rpx;
  line-height: 80rpx;
  margin: 30px auto;
  background: #55aaff !important;
  color: #FFFFFF !important;
  border-radius: 40rpx;
  font-size: 32rpx;
  font-weight: bold;
  border: none;
}

.province-next-button::after {
  border: none;
}

.province-next-button:active {
  opacity: 0.8;
}
</style>