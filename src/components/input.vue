<template>
    <div class="ipt_total" :class="[{'is_required':required,'b_red':isWarning,'b_color':show_ipt}]">
        <span class="c_red" v-if="required">*</span>
        <template v-if='show_ipt'>
            <transition name="fade" mode="in-out" appear>
                <div class="edit_content" >
                    <input :autofocus='{show_ipt}' :placeholder="placeholder" v-bind="$props" type="text" class="edit_input"
                           @keyup.13="save_input"
                           @focus="handleFocus"
                           @blur="handleBlur"
                           @input="handleInput"
                    >
                </div>
            </transition>
        </template>
        <template v-else>
            <transition name="fade" mode="out-in" appear>
                <div class="init_content"  >
                    <div class="ipt_title"  @click="edit_content">
                        <span class="c_primary" v-text='placeholder'>姓名</span>
                    </div>
                    <div class="ipt_content" @click="edit_content">
                        <p >{{currentValue}}</p>
                    </div>
                </div>
            </transition>
        </template>
    </div>
</template>
<style>
    .ipt_total{border:1px solid #ddd;border-radius:5px;height:60px;width:100%;padding:5px 5px 5px 10px;box-sizing:border-box;position:relative;}
    .ipt_title{height:20px;text-align:start}
    .c_primary{color:#54C08A;}
    .c_red{color:#f44455;font-size:1.6rem;position:absolute;right:8px;top:-3px;}
    .ipt_content{font-size:1.1em;text-align:start}
    .ipt_content p{height:23px;margin:0}
    .edit_input{height:48px;width:96%;padding:0 10px;font-size:1.5rem;border:0;}
    .b_red{border:1px solid #f44455}
    .b_color:{border:1px solid #54C08A!important}
</style>
<script>
    export default{
        props:{
            value:[String,Number],
            required: Boolean,
            placeholder: String,
            autofocus: Boolean,
        },
        data(){
            return{
                show_ipt:true,
                isWarning:false
            }
        },
        computed:{
            currentValue:function(){
                return this.value;
            },
        },
        mounted(){
            if(this.value){
                this.show_ipt=false;
            }else{
                this.show_ipt=true;
            }
        },
        methods:{
            handleInput(event) {
                let value = event.target.value;
                this.$emit('input', value);
                console.log(this.placeholder);
              },
            handleFocus(event) {
                this.$emit('focus', event);
            },
            handleBlur(event){
                this.$emit('blur', event);
                let value = event.target.value;
                if (this.required && !this.value) {
                  this.isWarning=true;
                  return false
                }else{
                    value ? this.show_ipt=false : this.show_ipt=true;
                }
            },
            edit_content(){
                this.show_ipt=true;
                this.handleFocus
            },
            save_input(event){
                let value = event.target.value;
                this.$emit('input', value);
                if(!value){
                    return false;
                }else{
                    this.show_ipt=false;
                }
            }

        },
        watch:{

        },
        components:{

        }
    }
</script>

