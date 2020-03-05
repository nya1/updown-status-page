<template>
  <div
    id="app"
    class="container"
  >
    <!-- header-->
    <div class="row align-items-center">
      <div class="col-md-12 text-center">
        <div class="top">
          <a :href="$config.website_url"><img
            v-if="typeof $config.logo_url !== 'undefined'"
            :src="$config.logo_url"
            :alt="$config.website_name"
            class="logotop"
          ></a>
          <h3>{{ $config.website_name }} Status Page</h3>
        </div>
      </div>
    </div>
    <!-- content -->
    <StatusPage />
    <!-- footer -->
    <div class="row text-center footer">
      <div
        v-if="typeof $config.website_url === 'string'"
        class="col"
      >
        <a :href="$config.website_url">&#8249; Home</a>
      </div>
      <div
        v-if="typeof $config.twitter === 'string'"
        class="col"
      >
        <a
          :href="'https://twitter.com/' + $config.twitter"
          target="_blank"
        ><img
          src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIAAAAyCAYAAAAeP4ixAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAAMqSURBVGhD7Zg7aBRBGMfX3TvBRrFQFMEHqFiIiDZ2QkC00cqAxCqYQkUQxMInIQRNIaYIiAFRUDGZWS6C2FloYWPlk4AgaqGixaF3N7OJz2z+s/ep590Y93ZnNxbzgz+7uex+r3nszDgWi8VisVhmi9LECpcH+z0mBz0uL7hMnirw2lbHDz16opUwnEN3CeFT89IbIcbkUgQ/4nHxAwmELWLyhceCnfR0nRuVhS6Xp5FsN/2SDBg56jExQH8mpsjEeth5q02gUUxMQWdUi7lc3MZ9gMTfOf7HBWQqGajSc+UAFTlOP7UPry1CQG9ago4jJr4gkY7ITuKegW4VVei34SGnN3Tpv7GBjYsNNuKLyTJapQv3O5DMpWgcJWK0urbZOLraXYcHy+iJf3O9PB+JfG62E09C/rxX44QsJgAD7U/DJFUpJnvitI7Hg11aG21JnE094cDQh1bDdblMPEK1O2eaNtE1DuvejSUmvkcFMwGqf17rpFFMvELV+osjYgO99gskckj7ThwxWSEzBvAnlsNotcXJ38TEe7TULVz70K/34TqgfS6OYIuiMAMC2wOjjbNXPsIHkkJIR5HJTVTdTlT3JLrPV63DjBTNkEbw5RKdg/wkhimS9KAqz/ROspcaYxRGelxeO6BzkoecUnUNhWGAe2EBU+gDnaNMxeQ4RWCQ+vI7WjzmJXwIe8m7YeprpsvQN51jo8KKVxWPPBtmdHJl0ZcbMR3vxSB8og3AmMQV8mqeAgu26J0aFlbKaitMbrMBjvwWx8Yl+sldhmC7iRnssT6A9MIAf4qV9FzyljHqMICJm7pAUkmtdEu1deQlP9S2E/35GrrC6/RrMLzffHqSNwiiAwm91AcYQ9g8eby2m8zlT3S8w8VVBJJ8eY/uBG0nkzmCPuyy2kEMyjupEoAwaTzMZ0zwyVWo+DCCvk/Lk/i7xJnEpMAH9YRaw5GnHOgNXSTSraZFbVDtiMlP0KAzJhaT9dmh6AebEdAQghlHS+nPbpvFZBli6EZd0Rnyfwc+jEhmG1qqx/XlMYyXc6rauPYh6CPqLMvhldVJTiUtFovFYrFYHGcazS5/dDE9KGwAAAAASUVORK5CYII="
          width="30px"
        >@{{ $config.twitter }}</a>
      </div>
    </div>
  </div>
</template>

<script>
import StatusPage from './components/StatusPage'

export default {
  name: 'App',
  components: {
    StatusPage
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.logotop {
  max-height: 80px;
  margin-bottom: 20px;
}
.top {
  padding: 20px 0;
  padding-top: 0px;
}
.footer {
  padding: 35px 0 20px 0;
}
</style>
