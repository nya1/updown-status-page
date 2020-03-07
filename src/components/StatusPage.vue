<template>
  <div>
    <div class="row align-items-center">
      <div class="col-md-12 text-center">
        <div v-if="loading === true">
          <p class="text-muted center-text">
            Loading, please wait...
          </p>
        </div>
        <div v-else-if="error !== false">
          <p class="center-text">
            An error occured {{ error.message || error }}
          </p>
        </div>
        <div v-else-if="checks === null || checks.length === 0">
          <p class="center-text">
            No checks found
          </p>
        </div>
        <div v-else>
          <hr>
          <div
            v-for="(thisCheck, index) in checks"
            :key="index + '_check'"
          >
            <div class="card-body">
              <div class="row align-items-center justify-content-center main no-gutters text-center">
                <div class="col-md-1 col-sm-3 align-self-center">
                  <span
                    v-if="thisCheck.down === false"
                    class="box up"
                  >UP</span>
                  <span
                    v-else
                    class="box dw"
                  >DOWN</span>
                </div>
                <div class="col-md-5 col-sm-10 text-left checkTitle">
                  <h5 class="card-title">
                    {{ thisCheck.alias || thisCheck.url }}
                  </h5>
                  <h6 class="card-subtitle mb-2 text-muted">
                    <a
                      class="nolink"
                      :href="'https://updown.io/' + thisCheck.token"
                      target="_blank"
                    >Last check: {{ toHumanDate(thisCheck.last_check_at) }}</a>
                  </h6>
                </div>
                <div
                  id="uptime"
                  class="col-md-2"
                >
                  <div class="uptime">
                    <p class="text-muted desc">
                      Uptime
                    </p>
                    <span>{{ thisCheck.uptime + '%' }}</span>
                  </div>
                </div>
                <div class="col-md-1">
                  <a
                    class="morelink"
                    :href="'https://updown.io/' + thisCheck.token"
                    target="_blank"
                  >Details →</a>
                </div>
              </div>
            </div>
            <hr>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ago from 's-ago';

export default {
  data () {
    return {
      checks: [],
      loading: true,
      error: false,
      lastPageUpdate: null,
    }
  },
  mounted () {
    // fetch all checks
    this.fetchChecks();
  },
  methods: {
    async getChecks() {
      const data = await window.fetch('https://updown.io/api/checks?api-key=' + this.$config.updown_read_key);
      return data.json();
    },
    async fetchChecks () {
      try {
        // call updown api to get all checks
        const checks = await this.getChecks();
        if (checks.length > 0) {
          // filter checks that are not published or enabled
          this.checks = checks.filter(c => {
            const isValid = c.enabled === true && c.published === true;
            return isValid;
          });
        }
        this.lastPageUpdate = new Date();
      } catch (e) {
        console.error(e);
        this.error = e;
      }
      this.loading = false;
    },
    /**
     * get human date like '5 minutes ago' by providing a ISO8601 date string
     */
    toHumanDate(stringDate) {
      // get human time
      const date = new Date(stringDate);
      return ago(date);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.center-text {
  padding: 10% 2%;
}
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
  margin-bottom: -5px;
}

@media only screen and (max-width: 769px) {
  .checkTitle {
    text-align: center !important;
  }
}
</style>
