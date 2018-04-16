<template>
  <div class="cf-component">
    <input type="submit" :value=local_label :class=local_classes :action=local_action :target=local_target :method=local_method :disabled=local_disabled></input>
  </div>
</template>

<script>
  export default {
    props: {
      label: {
        type: String,
        required: false,
        default: 'Submit',
      },
      classes: {
        type: String,
      },
      action: {
        // action page URL
        type: String,
      },
      target: {
        // where the response will be displayed
        type: String,
        default: '_self',
        validator: function(value) {
          return ['_blank', '_self', '_parent', '_top'].indexOf(value) !== -1;
        }
      },
      method: {
        type: String,
        default: 'GET',
        validator: function(value) {
          return ['GET', 'POST'].indexOf(value) !== -1;
        }
      },
      disabled: {
        type: Boolean,
        default: false
      }
    },
    /* data is included with props, because parent props can't be
     * mutated locally without affecting children. Use data instead. */
    data() {
      return {
        local_label: this.label,
        local_classes: this.classes,
        local_action: this.action,
        local_target: this.target,
        local_method: this.method,
        local_disabled: this.disabled,
      }
    }
  }
</script>

<style scoped>
  .cf-component {
    margin: 10px;
  }
  .cf-component input {
    color: #FFF;
    background-color: #23282D;
    font-weight: 900;
    height: 40px;
    margin: 10px;
    padding: 0px 25px 0px 25px;
    font-size: 14px;
    border-radius: 4px;
    transition: background-color .3s;
    -webkit-transition: background-color .3s; /* Safari */
  }
  .cf-component input:hover {
    background-color: #3CA3DC;
    background-color: #777;
  }
  .cf-component input:disabled {
    background-color: #CCC;
  }
</style>