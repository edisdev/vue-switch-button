<script>
export default {
  props: {
    switchValue: {
      type: Boolean,
      required: true
    },
    bgColor: {
      type: String,
      default: "#ccc9c9"
    },
    activeBgColor: {
      type: String,
      default: "#09f"
    },
    toggleColor: {
      type: String,
      default: "#fff"
    },
    toggleActiveColor: {
      type: String,
      default: "#fff"
    },
    width: {
      type: String,
      default: '90px'
    },
    height: {
      type: String,
      default: '45px'
    },
    toggleContent: {
      type: String,
      default: ''
    },
    toggleActiveContent: {
      type: String,
      default: ''
    },
    toggleFontSize: {
      type: String,
      default: ''
    },
    toggleFontColor: {
      type: String,
      default: ``
    },
    toggleActiveFontColor: {
      type: String,
      default: ``
    },
    toggleFontWeight: {
      type: String,
      default: 'normal'
    }
  },
  data() {
    return {
      toggleValue: this.switchValue
    };
  },
  watch: {
    toggleValue(value) {
      this.$emit('input', value);
    }
  },
  methods: {
    getSwitchStyle() {
      const style = {
        bgColor: this.toggleValue ? this.activeBgColor : this.bgColor,
        width: this.width,
        height: this.height,
        borderRadius: (this.width/3)
      };
      const customStyle = {
        'background': `${style.bgColor}`,
        'width': `${style.width}`,
        'height': `${style.height}`,
        'border-radius': `${parseInt(style.width)/3}px`,
      }
      return customStyle;
    },
    getToggleStyle() {
      const style = {
        toggleColor: this.toggleValue ? this.toggleActiveColor : this.toggleColor,
        width: parseInt(this.width)/3,
        height: parseInt(this.width)/3,
        top: parseInt(this.height) / 5,
        left: this.toggleValue ? ((parseInt(this.width)/3) + (parseInt(this.width)/5)) : (parseInt(this.width)/6),
        fontSize: this.toggleFontSize ? this.toggleFontSize : `${(parseInt(this.width)/3)}px`,
        color: this.toggleValue ? this.toggleActiveFontColor : this.toggleFontColor ,
        fontWeight: this.toggleFontWeight
      };
      const customStyle = {
        'background': `${style.toggleColor}`,
        'width': `${style.width}px`,
        'height': `${style.height}px`,
        'top': `${style.top}px`,
        'left': `${style.left}px`,
        'font-size': `${style.fontSize}`,
        'color': `${style.color}`,
        'font-weight': `${style.fontWeight}`
      };
      return customStyle;
    }
  }
};
</script>

<template>
  <div class="SwitchButton">
    <input id="switchInput" 
           type="checkbox"
           v-model="toggleValue">
    <label for="switchInput"  v-bind:style ="getSwitchStyle()">
       <div v-bind:style ="getToggleStyle()">
          <span v-if="toggleValue" v-html="toggleActiveContent"></span>
          <span v-else v-html="toggleContent"></span>
        </div>
    </label>
  </div>
</template>

<style lang="scss">

.SwitchButton {
  border: none;
  input {
    display: none;
    &,
    &:focus {
     outline: none;
     outline-color: transparent;
  }
  }
  label{
    position: relative;
    cursor: pointer;
    transition: all 500ms ease;
    display: flex;
      div {
        border-radius: 50%;
        z-index: 999;
        position: absolute;
        cursor: pointer;
        transition: left 500ms ease, color 500ms ease, transform 150ms ease;
        display: flex;
        align-items: center;
        justify-content: center;
        box-shadow: 0 3px 1px 0 rgba(0,0,0,.05), 0 2px 2px 0 rgba(0,0,0,.1), 0 3px 3px 0 rgba(0,0,0,.05)
    }
  }
}
</style>
