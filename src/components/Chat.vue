<template>
  <div class="chat">
    <div class="chat-top">
      <div class="chat-top__left">
        <img src="../image/avatar2.png" alt="Аватар" class="chat-top__left-image"/>
        <div class="chat-top__left-user">
          <span class="chat-top__left-user__name">Наталия Полянская</span>
          <div class="chat-top__left-user__descr">
            <img src="../image/flag.png" alt="Флаг" class="chat-top__left-user__descr-img"/>
            <span class="chat-top__left-user__descr-text"
              >Гид по Баварии, фотограф</span
            >
          </div>
        </div>
      </div>
      <div class="chat-top__right">
        <img src="../image/star.png" alt="Звезда" class="chat-top__right-img"/>
        <img src="../image/star.png" alt="Звезда" class="chat-top__right-img" />
        <img src="../image/star.png" alt="Звезда" class="chat-top__right-img" />
        <img src="../image/star.png" alt="Звезда" class="chat-top__right-img" />
        <img src="../image/staropacity.png" alt="Нет звезды" class="chat-top__right-img" />
      </div>
    </div>
    <div class="chat-messages">
      <div class="chat-messages__item" v-for="msg in messages" :key="msg">
        <div class="chat-messages__item-left">
          <img src="../image/avatar2.png" alt="Аватар" class="chat-messages__item-left__image">
        </div>
        <div class="chat-messages__item-right">
          <p class="chat-messages__item-right__text">{{ msg.text }}</p>
          <div class="chat-messages__item-right__time">Вчера в 18:45</div>
        </div>
      </div>
    </div>
    <div class="chat-bottom">
      <div class="chat-bottom__left">
        <img src="../image/avatar2.png" alt="Аватар" class="chat-bottom__left-image">
      </div>
      <div class="chat-bottom__right">
        <input type="text" v-model="inputText.text" placeholder="Напишите сообщение..." class="chat-bottom__right-input">
      </div>
      <button class="chat-bottom__button">
          <img src="../image/send.png" alt="Отправить" class="chat-bottom__button-img" @click="addToMsg">
        </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ChatSite",
  data () {
    return {
      inputText: {},
      messages: [
        {
          text: 'Из достопримечательностей могу предложить обратить внимание на вулкан Майон, путешествие запомнится вам надолго хотя бы из-за невероятной сложности подъема на него. Поверьте, это стоит того; также хотел бы отметить очень важную область исследования'
        },
        {
          text: 'Что из себя представляет вулкан? Просто хочу убедиться, что готова к такому путешествию.'
        },
        {
          text: 'Из достопримечательностей могу предложить обратить внимание на вулкан Майон, путешествие запомнится вам надолго хотя бы из-за невероятной сложности подъема на него. Поверьте, это стоит того; также хотел бы отметить очень важную область исследования'
        },
      ]
    }
  },
  methods: {
    addToMsg() {
      if (!this.inputText) {
        return;
      }

      this.messages.push(this.inputText);
      this.inputText = '';
      console.log(this.messages)
    }
  }
};
</script>
