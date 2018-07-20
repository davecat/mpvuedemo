<template>
  <div class="container main">
    <div class='buttonbox'>
      <div v-for="item in buttonArr">
        <div :id="item.key" :data-url='item.pathUrl' @click="clickItem" class='button-item'>
          <div class='button-box'>
            <img class='button-icon' :src="item.icon"/>
          </div>
          <div class='button-title'>{{item.title}}</div>
        </div>
      </div>
    </div>
    <div class='title-box'>
      <div style='font-size: 20px;'>本地房源</div>
      <div style='font-size: 14px;'
            @click='navcity'>北京市 ></div>
    </div>
    <block>
      <div class='buttonbox' style='justify-content: space-around;'>
        <div>
          <div class='button-info-title'>本周新增</div>
          <div style='flex-direction: row;display: flex;align-items: center;margin-top:10px;'>
            <!--<div class='button-info-text'>{{value}}</div>-->
            <div style='font-size:28px;margin-top:10px;'>100套</div>
          </div>
        </div>
        <div>
          <div class='button-info-title'>可租房源</div>
          <div style='flex-direction: row;display: flex;align-items: center;margin-top:10px;'>
            <!--<div class='button-info-text'>{{value}}</div>-->
            <div style='font-size:28px;margin-top:10px;'>30套</div>
          </div>
        </div>
        <div>
          <div class='button-info-title'>本周已租</div>
          <div style='flex-direction: row;display: flex;align-items: center;margin-top:10px;'>
            <!--<div class='button-info-text'>{{value}}</div>-->
            <div style='font-size:28px;margin-top:10px;'>10套</div>
          </div>
        </div>
      </div>

      <div v-for="item in housingList" class='cell-box' @click='navpage'>
        <div class='cell-img-box'>
          <img style="width: 178px;height: 110px;" class='bgimg' :src='item.picUrl' />
        </div>
        <div style='margin-left:10px;flex:1'>
          <div style='font-size:12px;'>{{item.rentalType+item.name+' '+item.address}}</div>
          <div style='font-size:12px;color:#999;margin-top:8px;'>
            {{(item.numberOfBedroom||'')+'室'+(item.numberOfLivingroom||'')+'厅 / '+(item.square||0)+' m2 / '+(item.communityName||'')}}
          </div>
          <div
            style='width:100%;margin-top:10px;margin-bottom:30px;flex-direction: row;display: flex;justify-content: space-between;'>
            <div style='color:#ee3535;font-size:12px;'>{{ (item.monthlyRent||'')+' / 月'}}</div>
            <div style='color:purple;font-size:12px;'>{{item.createdDate}}</div>
          </div>
        </div>
      </div>
      <div class='button-all' @click='nexthouse' >查看全部房源</div>
    </block>
  </div>
</template>

<script>

export default {

  data () {
    return {
      buttonArr: [
        {
          pathUrl: '',
          icon: require('../../images/home/agreement.png'),
          title: '签合同'
        },
        {
          pathUrl: '',
          icon: require('../../images/home/receipt.png'),
          title: '收款码'
        },
        {
          pathUrl: '',
          icon: require('../../images/home/house.png'),
          title: '查房源'
        }
      ],
      housingList: [
        {
          picUrl: require('../../images/1.jpg'),
          rentalType: '整租',
          name: '次卧',
          address: '北京市朝阳区',
          numberOfBedroom: 3,
          numberOfLivingroom: 2,
          square: 100,
          communityName: '潘家园社区',
          monthlyRent: 1000,
          createdDate: '本周上新'
        },
        {
          picUrl: require('../../images/2.jpg'),
          rentalType: '整租',
          name: '次卧',
          address: '河南郑州',
          numberOfBedroom: 1,
          numberOfLivingroom: 1,
          square: 29,
          communityName: '三里河',
          monthlyRent: 200,
          createdDate: '本周上新'
        },
        {
          picUrl: require('../../images/3.jpg'),
          rentalType: '整租',
          name: '次卧',
          address: '北京市丰台区',
          numberOfBedroom: 3,
          numberOfLivingroom: 2,
          square: 89,
          communityName: '万年花城',
          monthlyRent: 3700,
          createdDate: '本周上新'
        },
      ],
    }
  },

  created () {

  }
}
</script>

<style>
  .main{
    padding: 20px 15px;
  }
  .buttonbox{
    width: 100%;
    display: flex;
    margin-top: 10px;
    flex-direction: row;
    align-items: center;
    text-align: center;
    justify-content: space-around;
  }
  .button-box{
    width: 65px;
    height: 65px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .button-icon{
    width: 65px;
    height: 65px;
    background: transparent;
  }
  .button-item{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 80px;
    height: 90px;
  }
  .button-title{
    font-size: 14px;
    padding: 0 0;
    margin-top: 10px;
  }
  .title-box{
    width: 100%;
    height: 65px;
    margin-top: 10px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    border-bottom: 1px solid gainsboro;
  }
  .button-info-title{
    color: #999;
    font-size: 14px;
  }
  .button-info-text{
    font-size: 14px;
    line-height: 60px;
    flex:1
  }
  .cell-box{
    width: 100%;
    padding-top: 20px;
    flex-direction: row;
    display: flex;
    border-bottom: solid 1px #eee;
  }
  .cell-img-box{
    width: 178px;
    height: 110px;
    display: flex;
    align-items: center;
    justify-content: center;
    background:#ededed;
  }
  .cell-img{
    position: relative;
    width: 280px;
    height: 140px;
    z-index: 1;
  }
  .bgimg{
    width:30px;
    height:30px;
    position: absolute;
  }
  .button-all{
    font-size: 14px;
    height: 50px;
    width: 100%;
    background: #eee;
    align-items: center;
    justify-content: center;
    text-align: center;
    line-height: 50px;
    border-radius: 10px;
    margin-top: 20px;
    color: purple;
  }
  .locerror{
    width: 100vw;
    height: 50vh;
    color: #999;
    font-size: 16px;
    text-align: center;
    line-height: 50vh;
  }
</style>
