<template>
    <li>
        <base-card>
            <header>
                <h3>{{ resObj.title }}</h3>
                <base-button mode="flat" @click="removeRes(resObj.id)">Delete</base-button>
            </header>
            <p>{{ resObj.description }}</p>
            <nav>
                <a :href="resObj.resourceLink">View Resource</a>
            </nav>
        </base-card>
    </li>
</template>

<script>
    export default {
        name: 'ResourceItem',
        props: ['resObj'],
        inject: ['removeRes'],
    }
</script>

<style scoped>
li {
  margin: auto;
  max-width: 40rem;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h3 {
  font-size: 1.25rem;
  margin: 0.5rem 0;
}

p {
  margin: 0.5rem 0;
}

a {
  text-decoration: none;
  color: #ce5c00;
}

a:hover,
a:active {
  color: #c89300;
}
</style>