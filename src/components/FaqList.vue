<template>
  <div id="faqlist-wrapper">
    <h2>{{ title }}</h2>
    <Faq v-for="faq in faqs" :question="faq.question" :answer="faq.answer" />
  </div>
</template>

<script>
import Faq from "./Faq.vue";
export default {
  data() {
    return {
      faqs: [
        {
          question: "Who do I contact about a refund or an invoicing inquiry?",
          answer:
            "If you would like to inquire about a refund or anything to do with your invoice, please contact the booking site directly. They are responsible for the booking and payment process, so will be in the best position to help you. As a metasearch, trivago is not directly involved in the booking or payment process. Your booking confirmation will include their contact details.",
        },
        {
          question: "Who do I contact about a refund or an invoicing inquiry?",
          answer:
            "If you would like to inquire about a refund or anything to do with your invoice, please contact the booking site directly. They are responsible for the booking and payment process, so will be in the best position to help you. As a metasearch, trivago is not directly involved in the booking or payment process. Your booking confirmation will include their contact details.",
        },
        {
          question: "Who do I contact about a refund or an invoicing inquiry?",
          answer:
            "If you would like to inquire about a refund or anything to do with your invoice, please contact the booking site directly. They are responsible for the booking and payment process, so will be in the best position to help you. As a metasearch, trivago is not directly involved in the booking or payment process. Your booking confirmation will include their contact details.",
        },
        {
          question: "Who do I contact about a refund or an invoicing inquiry?",
          answer:
            "If you would like to inquire about a refund or anything to do with your invoice, please contact the booking site directly. They are responsible for the booking and payment process, so will be in the best position to help you. As a metasearch, trivago is not directly involved in the booking or payment process. Your booking confirmation will include their contact details.",
        },
      ],
    };
  },
  props: ["title"],
  components: { Faq },
};
</script>

<style scoped>
h2 {
  padding: 0.5% 5%;
  margin: 2% 7%;
  font-size: 2.1em;
}
#faqlist-wrapper {
  min-width: 71%;
}
</style>