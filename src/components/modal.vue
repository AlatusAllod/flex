<template>
  <div :class="[$style.blocker, {[$style.blocker__active]: active}]" @click="active = false">
    <div :class="[$style.modal, {[$style.active]: active}]">
      <h1 :class="$style.title">Здравствуйте, Дмитрий.</h1>
      <p :class="$style.text">Мы получили ваш макет.
        <br>Нам всё очень понравилось, но мы не уверены относительно расположения элементов. Не могли бы вы поиграться с их позицией? Мы бы хотели получить что-то более интригующее, чем сейчас.
        <br>И цвета, Дмитрий, цвета! Наступает весна и мы хотели бы, чтобы люди радовались, заходя на наш сайт с продающими квадратами. Мы понимаем, что вы программист, а не дизайнер, но, может быть, вы всё же смогли бы удивить нас вашей творческой искрой, вы же профессионал в конце концов.
        <br>С уважением, студент группы Frontend-разработка, Романов Роман Андреевич и его кот.
      </p>
    </div>
  </div>
</template>

<script>
export default {
  mounted() {
    setTimeout(() => {
      this.active = true;
    }, 500);
  },
  data() {
    return {
      active: false
    };
  }
};
</script>

<style lang="sass" module>
  .blocker 
    /* Positining */
    position: fixed
    top: 0
    left: 0
    z-index: 1

    /* Display & Box Model */
    width: 100%
    height: 100%
    opacity: 0

    /* Color */
    background-color: rgba(0, 0, 0, 0.5)

    /* Other */
    transition: opacity 0.5s
    cursor: pointer
    pointer-events: none

  .blocker__active
    /* Positining */
    opacity: 1
    
    /* Other */
    pointer-events: all

  .modal
    /* Display and Box Model */
    box-sizing: border-box
    max-width: 800px
    max-height: 600px
    margin: auto
    padding: 40px
    border: none
    border-radius: 40px
    opacity: 0
    overflow: auto
    transform: translateY(300px)

    /* Positioning */
    position: fixed
    left: 0
    top: 0
    right: 0
    bottom: 0
    z-index: 2

    /* Color */
    background-color: #fff

    /* Other */
    pointer-events: none
    transition-property: opacity, transform
    transition-duration: 0.5s

  .active 
    /* Display and Box Model */
    opacity: 1
    transform: translateY(0px)

    /* Other */
    pointer-events: all
  
  .title
    /* Display and Box Model */
    text-align: center

  .text
    /* Text */
    font-size: 22px
    line-height: 1.5
</style>
