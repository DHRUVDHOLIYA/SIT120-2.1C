<template>
  <div class="gym-app">
    <!-- Conditional Rendering -->
    <div class="welcome" v-if="showWelcome">
      <h1>Welcome to our Gym!</h1>
    </div>
    <div class="thanks" v-else>
      <h1>Thanks for visiting our Gym!</h1>
    </div>
    
    <div class="details" v-show="showDetails">
      <h2>Your Gym Details:</h2>
      <ul>
        <li v-for="(value, label) in userGymDetails" :key="label">{{ label }}: {{ value }}</li>
      </ul>
    </div>
    
    <!-- Form Input Handling -->
    <form @submit.prevent="submitForm" class="user-form">
      <label for="name">Name:</label>
      <input type="text" v-model="userGymDetails.name" required>
      
      <label for="age">Age:</label>
      <input type="number" v-model="userGymDetails.age" required>
      
      <label for="gender">Gender:</label>
      <select v-model="userGymDetails.gender" required>
        <option value="male">Male</option>
        <option value="female">Female</option>
        <option value="other">Other</option>
      </select>
      
      <label for="membership">Membership Type:</label>
      <select v-model="userGymDetails.membership" required>
        <option value="basic">Basic</option>
        <option value="premium">Premium</option>
      </select>
      
      <label for="payment">Payment Method:</label>
      <div class="payment-options">
        <label>
          <input type="radio" value="creditCard" v-model="userGymDetails.payment">
          Credit Card
        </label>
        <label>
          <input type="radio" value="paypal" v-model="userGymDetails.payment">
          PayPal
        </label>
      </div>
      
      <button type="submit">Submit</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showWelcome: true,
      showDetails: false,
      userGymDetails: {
        name: '',
        age: null,
        gender: '',
        membership: 'basic',
        payment: ''
      }
    };
  },
  methods: {
    submitForm() {
      this.showWelcome = false;
      this.showDetails = true;
    }
  }
};
</script>

<style>
.gym-app {
  text-align: center;
  padding: 20px;
}

.welcome {
  background-color: #ffd700;
  padding: 10px;
  border-radius: 5px;
  margin-bottom: 20px;
}

.thanks {
  background-color: #90ee90;
  padding: 10px;
  border-radius: 5px;
  margin-bottom: 20px;
}

.details {
  display: none;
  background-color: #87ceeb;
  padding: 10px;
  border-radius: 5px;
}

.user-form {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #f0f0f0;
  padding: 20px;
  border-radius: 5px;
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
}

label {
  font-weight: bold;
  margin-bottom: 5px;
}

input,
select {
  padding: 8px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 3px;
}

button {
  padding: 10px 20px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 3px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

.payment-options {
  display: flex;
  align-items: center;
  margin-top: 5px;
}

.payment-options label {
  display: flex;
  align-items: center;
  margin-right: 15px;
}

.payment-options input[type="radio"] {
  margin-right: 5px;
}

</style>
