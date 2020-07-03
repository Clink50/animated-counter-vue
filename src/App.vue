<template>
  <div id="app">
    <header>
      <div class="container">
        <h1>Animated Counter</h1>
      </div>
    </header>
    <section class="counters">
      <div class="container">
        <Counter
          v-for="counter in counters"
          :key="counter.id"
          :icon="counter.icon"
          :target="counter.target"
          :initial="counter.initial"
          :description="counter.description"
        />
      </div>
    </section>
  </div>
</template>

<script>
import Counter from './components/Counter.vue';

export default {
  name: 'App',
  components: {
    Counter,
  },
  data() {
    return {
      counters: [
        {
          id: '1',
          icon: 'fa-youtube',
          target: '60000',
          initial: '0',
          description: 'Subscribers',
        },
        {
          id: '2',
          icon: 'fa-twitter',
          target: '15000',
          initial: '0',
          description: 'Followers',
        },
        {
          id: '3',
          icon: 'fa-facebook',
          target: '9000',
          initial: '0',
          description: 'Facebook',
        },
        {
          id: '4',
          icon: 'fa-linkedin',
          target: '5000',
          initial: '0',
          description: 'Connections',
        },
      ],
    };
  },
  created() {
    const speed = 200; // Lower = faster

    this.counters.forEach((counter) => {
      const updateCount = () => {
        const target = +counter.target;
        const count = +counter.initial;
        const increment = counter.target / speed;

        if (count < counter.target) {
          counter.initial = Math.ceil(count + increment);
          setTimeout(updateCount, 1);
        } else {
          counter.initial = target;
        }
      };

      updateCount();
    });
  },
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Roboto&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#app {
  font-family: 'Roboto', sans-serif;
  background: lightskyblue
    url('https://i.pinimg.com/originals/3c/24/46/3c24462450c2a902bf7e18f3d9aada81.jpg');
  color: #fff;

  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  height: 100vh;
}

header {
  flex: 1;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;

  .container {
    max-width: 1100px;
    margin: 0 auto;
    overflow: auto;

    h1 {
      font-size: 60px;
    }
  }
}

.counters {
  background: #0f479a;
  color: #fff;
  padding: 40px 20px;
  border-top: 3px solid lightskyblue;

  .container {
    display: grid;
    grid-gap: 30px;
    grid-template-columns: repeat(4, 1fr);
    text-align: center;
  }
}

/* Anything under 700px */
@media (max-width: 700px) {
  .counters .container {
    grid-template-columns: repeat(2, 1fr);
  }

  .counters .container > div:nth-of-type(1),
  .counters .container > div:nth-of-type(2) {
    border-bottom: 1px solid lightskyblue;
    padding: 20px;
  }
}
</style>
