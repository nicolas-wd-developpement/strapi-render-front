<template>
<div>
  <header>
    <!-- Navbar -->
    <MDBNavbar expand="lg" light bg="white" container>
      <MDBNavbarToggler target="#navbarExample01"></MDBNavbarToggler>
      <MDBNavbarNav collapse="navbarExample01" class="mb-2 mb-lg-0">
        <MDBNavbarItem to="#" active>
          Home
        </MDBNavbarItem>
        <MDBNavbarItem to="#">
          Features
        </MDBNavbarItem>
        <MDBNavbarItem to="#">
          Pricing
        </MDBNavbarItem>
        <MDBNavbarItem to="#">
          About
        </MDBNavbarItem>
      </MDBNavbarNav>
    </MDBNavbar>
    <!-- Navbar -->
    <!-- Jumbotron -->
    <div class="p-5 text-center bg-light">
      <h1 class="mb-3">Tag Items</h1>
      <h4 class="mb-3">Subheading</h4>
      <a class="btn btn-primary" href="" role="button"
        >Call to action</a
      >
    </div>
    <!-- Jumbotron -->
  </header>
<div v-if="tags.length">
  <MDBRow :cols="['1','md-4']" class="g-4">
  <div v-bind:key="tag.index" v-for="tag in tags">
    <MDBCol>
      <MDBCard>
        <MDBCardImg :src="imageLink + tag.image" top alt="..."/>
        <MDBCardBody>
          <MDBCardTitle>{{tag.name}}</MDBCardTitle>
          <MDBCardText>
            {{tag.email}}
          </MDBCardText>
        </MDBCardBody>
      </MDBCard>
    </MDBCol>
  </div>
  </MDBRow>
  </div>
</div>
</template>

<script>
import { MDBNavbar, MDBNavbarToggler, MDBNavbarNav, MDBNavbarItem, MDBCol, MDBRow, MDBCard, MDBCardBody, MDBCardTitle, MDBCardText, MDBCardImg } from 'mdb-vue-ui-kit';
export default {
  name: 'HelloWorld',
  components: {
    MDBNavbar,
    MDBNavbarToggler,
    MDBNavbarNav,
    MDBNavbarItem,
    MDBCol,
    MDBRow,
    MDBCard,
    MDBCardBody,
    MDBCardTitle,
    MDBCardText,
    MDBCardImg
  },
  data(){
    return {
      tags: [],
      imageLink: "http://localhost:1337/api/tags"
    }
  },
    mounted() {
    fetch("http://localhost:1337/api/tags")
      .then((res) => res.json())
      .then((data) => {
        this.tags = data;
      });
  }
}
</script>