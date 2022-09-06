<template>
  <main id="container">
    <h1>Resume</h1>
    <h2>Muhammad Reynaldi</h2>
    <p>
      Lorem ipsum dolor sit amet, consectetur adipisicing elit. Fugiat,
      necessitatibus eligendi perspiciatis ea delectus ut accusamus praesentium
      sunt reprehenderit! Mollitia!
    </p>
    <section id="satu">
      <h2>Experience</h2>
      <div v-for="(data, index) in experiences" :key="data.id">
        <p @click="showDesc(data)">
          {{ index + 1 }}. {{ data.start }} - {{ data.end }},
          {{ data.position }} at
          {{ data.company }}
        </p>
        <p v-if="data.show">{{ data.description }}</p>
      </div>
    </section>
    <section id="2">
      <h2>Skills</h2>
      <ul v-for="data in skills" :key="data.id">
        <li>{{ data.name }}</li>
        <div
          class="percentage"
          :style="{
            width: data.percentage + '%',
          }"
        >
          {{ data.percentage }}
        </div>
      </ul>
    </section>
    <section id="3">
      <h2>Contact Me</h2>
      <form>
        <p>Name:</p>
        <input type="text" v-model="contact.name" required />
        <p>Email:</p>
        <input type="email" v-model="contact.email" required />
        <p>Note:</p>
        <textarea v-model="contact.note" required />
        <button @click="submitContact()">Send</button>
      </form>
    </section>
  </main>
</template>

<script>
export default {
  data() {
    return {
      experiences: [
        {
          id: 1,
          start: "Aug 2022",
          end: "Present",
          position: "Frontend Engineer",
          company: "PT. Qatros Teknologi Nusantara",
          description:
            "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Fugiat, necessitatibus eligendi perspiciatis ea delectus ut accusamus praesentium sunt reprehenderit! Mollitia!",
          show: false,
        },
        {
          id: 2,
          start: "Apr 2022",
          end: "Jul 2022",
          position: "Web Developer Internship",
          company: "PT. Djitu Global International",
          description:
            "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Fugiat, necessitatibus eligendi perspiciatis ea delectus ut accusamus praesentium sunt reprehenderit! Mollitia!",
          show: false,
        },
        {
          id: 3,
          start: "Feb 2022",
          end: "July 2022",
          position: "Front End Javascript",
          company: "Binar Academy",
          description:
            "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Fugiat, necessitatibus eligendi perspiciatis ea delectus ut accusamus praesentium sunt reprehenderit! Mollitia!",
          show: false,
        },
      ],
      skills: [
        {
          id: 1,
          name: "React.js",
          percentage: 76,
        },
        {
          id: 2,
          name: "Next.js",
          percentage: 60,
        },
        {
          id: 3,
          name: "Vue.js",
          percentage: 40,
        },
      ],
      contact: {
        name: "",
        email: "",
        note: "",
      },
    };
  },
  methods: {
    showDesc(data) {
      data.show = !data.show;
    },
    submitContact() {
      alert(
        "Terimakasih " +
          this.contact.name +
          " dengan " +
          this.contact.email +
          "mengirimkan note " +
          this.contact.note
      );
    },
  },
};
</script>

<style>
* {
  font-family: "Poppins", sans-serif;
}

main#container {
  padding: 20px;
  margin-left: auto;
  margin-right: auto;
  margin-top: 0;
  margin-bottom: 0;
  width: 50%;
  height: 100%;
  background-color: gray;
  color: white;
}

.percentage {
  background-color: #00ff33;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 30px;
  border-radius: 6px;
}

form {
  background-color: black;
  border-radius: 5px;
  padding: 20px;
  background-color: rgb(96, 96, 96);
}

form input {
  width: 100%;
  height: 20px;
  border-radius: 2px;
  border: none;
}

form textarea {
  width: 100%;
  height: 120px;
  border-radius: 2px;
  border: none;
}

form button {
  margin-top: 10px;
  display: block;
  border-radius: 5px;
  padding: 8px 15px;
  background-color: #00ff33;
  border: none;
}

section#satu div p {
  cursor: pointer;
}
</style>
