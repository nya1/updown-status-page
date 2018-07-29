<template>
  <div class="container">
    <div class="row align-items-center">
      <div class="col-md-12">
        <div class="top">
          <a :href="config.website_url"><img v-if="typeof config.logo_url !== 'undefined'" :src="config.logo_url" :alt="config.website_name" class="logotop" /></a>
          <h3>{{config.website_name}} Status page</h3>
        </div>

        <div v-for="(thisCheck, index) in checks">
          <div class="card-body">

            <div class="row align-items-center justify-content-center main no-gutters text-center">
              <div class="col-md-1 col-sm-1 align-self-center">
                  <span v-if="thisCheck.down === false" class="box up">UP</span>
                  <span v-else class="box dw">DOWN</span>
              </div>
              <div class="col-md-5 col-sm-8 text-left">
                <h5 class="card-title">
                  {{thisCheck.alias || thisCheck.url}}
                </h5>
                <h6 class="card-subtitle mb-2 text-muted">
                  <a class="nolink" :href="'https://updown.io/' + thisCheck.token" target="_blank">Last check: {{thisCheck.last_check_at}}</a>
                </h6>
              </div>
              <div class="col-md-2" id="uptime">
                <div class="uptime">
                  <span class="text-muted desc">Uptime</span>
                  <p>{{thisCheck.uptime + '%'}}</p>
                </div>
              </div>
              <div class="col-md-1">
                <a class="morelink" :href="'https://updown.io/' + thisCheck.token" target="_blank">Details →</a>
              </div>
            </div>
          </div>
          <hr v-if="index < checks.length-1"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
const config = require('../../page_config.json')
const Updown = require('node-updown');
const ud = new Updown(config.updown_read_key);
export default {
  name: 'HelloWorld',
  data () {
    return {
      config,
      checks: []
    }
  },
  mounted () {
    // fetch all checks
    this.fetchChecks()
  },
  methods: {
    fetchChecks: async function () {
      try {
        let checks = await ud.getChecks()
        if (checks.length > 0) {
          this.checks = checks
        }
      } catch (e) {
        console.error(e)
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.up {
  background-color: #17b96e;
}
.box {
  padding: 5px;
  margin-bottom: 2px;
  font-size: 0.7em;
  color: #FFF;
  border-radius: 3px;
  text-align: center;
  vertical-align: text-top;
}
.dw {
  background-color: #ff0a0a;
}
h5 {
  font-size: 1.15em;
}
.nolink {
  text-decoration: none;
  color: #6c757d;
}
h6 {
  font-size: 0.75em;
}
.uptime {
  font-size: 1.35em;
  color: #333;
}
.morelink {
  font-size: 0.75em;
}
.main {
  font-size: 1.4em;
}
.desc {
  font-size: 0.75em;
}
.logotop {
  max-height: 80px;
  margin-bottom: 20px;
}
.top {
  padding: 20px 0;
}
</style>
