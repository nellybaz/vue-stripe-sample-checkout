<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div>
    <stripe-checkout
      ref="checkoutRef"
      :pk="publishableKey"
      :session-id="sessionId"
    />
    <button style="padding:10px" @click="submit">PAY WITH STRIPE</button>
  </div>
  </div>
</template>

<script>
import { StripeCheckout } from "@vue-stripe/vue-stripe";
export default {
  components: {
    StripeCheckout,
  },
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    this.publishableKey = "pk_test_51J00Y7A0wYRZlPRCBjv4mKpsSHBEdKWffvrHBE6dzs1gKLRdp2tisGnJklZjD5e3aFwYGY40zbpMLLqh2w54RbFe00VLJ8vP4x";
    return {
      loading: false,
      sessionId: 'cs_test_a1SRbQSS8iDC3nQUwLcZzBOKrjlJNciZip7D7foMpyfXNIjYyrpKzLoKme', // session id from backend
    };
  },
  methods: {
    submit() {
      // You will be redirected to Stripe's secure checkout page
      this.$refs.checkoutRef.redirectToCheckout();
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
