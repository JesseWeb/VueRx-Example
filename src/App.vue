<template>
  <div id="app">
    {{vueRxCount}}
    {{count}}
  </div>
</template>

<script>
import { Observable} from 'rxjs/Observable';
import 'rxjs/add/observable/interval';
import 'rxjs/add/operator/filter';
export default {
  name: 'App',

  data(){
    return {
      count:0
    }
  },
  // use vue-rx
  subscriptions(){
    return{
      //在使用vue-rx时,不需要subscribe
      vueRxCount:Observable.interval(1000).filter((value) => {
        return value % 2 ===0
      })
    }
  },
  created(){
    //普通方式使用rxjs 需要使用subscribe 
    const obs = Observable.interval(1000)
    obs.subscribe((value) => {
      this.count = value
    })
  }
}
</script>

<style>

</style>
