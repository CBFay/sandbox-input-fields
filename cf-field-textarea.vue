<template>
  <div class="cf-component">
    <div class="fieldheader cf"> <span class="label cf"> {{ local_label }}</span> <span class="errormessage cf">{{ local_description }}</span></div>
    <textarea type="textarea" :placeholder=local_placeholder :required=local_required :minlength=local_minlength :maxlength=local_maxlength :pattern=local_pattern :class=local_classes></textarea>
    <button class="cf textarea-field-icon-edit">&#xe020;</button>
  </div>
</template>

<script>
  export default {
    props: {
      // Using prop objects instead of an Array allows validation and default control
      label: {
        type: String,
        required: false,
        default: 'Paragraph Text'
      },
      placeholder: {
        type: String,
      },
      classes: {
        type: String,
      },
      required: {
        type: Boolean,
        default: false,
      },
      minlength: {
        type: Number,
      },
      maxlength: {
        type: Number,
      },
      pattern: {
        // validation regex
        type: String,
      },
      description: {
        // desribe valid input
        type: String,
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
        local_minlength: this.minlength,
        local_maxlength: this.maxlength,
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
  .cf-component textarea {
    color: #333;
    font-size: 16px;
    font-weight: 500;
    vertical-align: top;
    width: 388px;
    height: 96px;
    margin: 10px;
    padding: 14px 0px 0px 10px;
    border-radius: 5px;
    min-width: 390px;
    border-width: 1px;
    border-color: rgba(0, 0, 0, 0.2);
    transition: border-color 1.5s;
    -webkit-transition: border-color 1.5s; /* Safari */
    max-width: 460px;
    min-height: 34px;
  }
  .cf textarea:focus {
    border-width: 2px;
    border-color: rgba(0, 0, 0, 0.3);
    margin: 9px 9px 9px 9px;
  }
</style>