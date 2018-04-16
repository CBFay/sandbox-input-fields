<template>
  <div class="cf-component">
    <div class="fieldheader cf"> <span class="label cf"> {{ local_label }}</span> <span class="errormessage cf">{{ local_description }}</span></div>
    <input type="text" :placeholder=local_placeholder :class=local_classes :required=local_required :pattern=local_pattern></input>
    <button class="cf text-field-icon-edit">&#xe020;</button>
  </div>
</template>

<script>
  export default {
    props: {
      label: {
        type: String,
        required: false,
        default: 'Single Line Text',
      },
      placeholder: {
        type: String,
      },
      classes: {
        type: String,
      },
      required: {
        type: Boolean,
        default: false
      },
      pattern: {
        // validation regex
        type: String,
      },
      description: {
        // desribe valid input
        type: String
      }
    },
    /* data is included with props, because parent props can't be
     * mutated locally without affecting children. Use data instead. */
    data() {
      return {
        local_label: this.label,
        local_placeholder: this.placeholder,
        local_classes: this.classes,
        local_required: this.required,
        local_pattern: this.pattern,
        local_description: this.description,
      }
    }
  }
</script>

<style scoped>
  .cf .label {
    margin: 0px 0px 0px 15px;
    font-weight: bold;
  }
  .cf .errormessage {
    color: #ffa31a;
  }
  .cf-component input {
    color: #333;
    font-weight: 500;
    width: 388px;
    height: 48px;
    margin: 10px;
    font-size: 16px;
    padding: 0px 0px 0px 10px;
    border-radius: 5px;
    border-width: 1px;
    border-color: rgba(0, 0, 0, 0.2);
    transition: border-color 1.5s;
    -webkit-transition: border-color 1.5s; /* Safari */
  }
  .cf input:focus {
    border-width: 2px;
    border-color: rgba(0, 0, 0, 0.3);
    margin: 9px;
  }

</style>

