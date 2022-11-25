<template>
  <div class="container">
    <p>
      Количество монет:
      <span>{{ money }}</span>
    </p>
    <hr>
    <p>Количество кликов:
      <span>{{ clicks }}</span>
    </p>
    <button @click="click">
      Кликнуть
    </button>

    <hr>
    <p>Цена апгрейда:
      <span>{{ upgradeCost }}</span>
    </p>
    <button @click="buyPowerUpgrade">
      Купить апгрейд
    </button>

  </div>
</template>

<script>
export default {
  data: () => {
    return {
      money: 0,
      clicks: 0,
      clickPower: 1,
      upgradeCost: 6,
      CLICK_UPGRADE: 1,
      MONEY_INCOME: 2

    };
  },
  methods: {
    click() {
      if (this.clicks >= 5) {
        this.money += this.MONEY_INCOME;
        this.clicks = 0;
      }
      this.clicks += this.clickPower;
    },
    buyPowerUpgrade() {
      if (this.money < this.upgradeCost) {
        return alert('Нехватает средств')
      }
      this.clickPower += this.CLICK_UPGRADE;
      this.money -= this.upgradeCost
      this.upgradeCost *= 2;
    }

  }
}
</script>

<style>

:root {
  background: aliceblue;
}

.container {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

hr {
  width: 200px;
}

p {
  background: lightgray;
  padding: 20px;
}

</style>
