<template>
<div class="eos container">
      <h1>Eos Demo</h1>
      <div class="row">
          <div class="proposer col-sm-2">
              <button type="button"> Select files</button>
          </div>

          <div class="approver col-sm-3">
              <button type="button"> A</button>
              <input type="text" name="a" class="form-control" placeholder="Private Key">
              <div class="input-group-append">
                  <button class="btn btn-primary" type="button">OK</button>
              </div>
          </div>

          <div class="approver col-sm-3">
              <button type="button">B</button>
              <input type="text" name="b" class="form-control" placeholder="Private Key">
              <div class="input-group-append">
                  <button class="btn btn-primary" type="button">OK</button>
              </div>
          </div>
          <div class="approver col-sm-3">
              <button type="button" >C</button>
              <input type="text" name="c" class="form-control" placeholder="Private Key">
              <div class="input-group-append">
                  <button class="btn btn-primary" type="button">OK</button>
              </div>
          </div>
      </div>
  </div>
</template>

<script>
// import * as Eos from 'eosjs'
const Eos = require('eosjs')
const config = {
  expireInSeconds: 600,
  broadcast: true,
  // debug: false,
  httpEndpoint: 'https://api-kylin.eosasia.one:443',
  // mainNet chainId
  chainId: 'cf057bbfb72640471fd910bcb67639c22df9f92470936cddc1ade0e2f2e7dc4f',
  keyProvider: '5JtBjNpWk6AwjnaxbkJ9yftMFcDH5MzxFHsPaVbkLYQy5S82Sgf',
  sign: true
}
const eos = Eos(config)
export default {
  data () {
    return {
      title: 'eosjs test app',
      privateKey: '',
      masterPrivate: '5KQwrPbwdL6PhXujxW37FSSQZ1JiwsST4cqQzDeyXtP79zkvFD3',
      httpEndpoint: 'https://api-kylin.eosasia.one:443',
      keyProvider: '5KQwrPbwdL6PhXujxW37FSSQZ1JiwsST4cqQzDeyXtP79zkvFD3',
      chainId: null,
      keyPair: {
        private: '',
        public: ''
      },
      newAccount: {
        login: '',
        password: '',
        result: ''
      },
      accountInfo: {
        name: '',
        info: ''
      },
      accountBalance: {
        name: '',
        info: ''
      },
      accountHistory: {
        name: '',
        info: ''
      },
      issueToken: {
        name: '',
        amount: '',
        result: ''
      },
      sendToken: {
        password: '',
        from: '',
        to: '',
        amount: '',
        result: ''
      },
      eos: null
    }
  },
  mounted () {
    Eos().getInfo((error, info) => {
      console.log('95>>>', info)
      console.log(error, info)
    })
    eos.getBlock(1)
      .then((result) => {
        console.log('100>>>')
        console.log(result)
      })
      .catch(error => console.error(error))

    console.log('105****', eos.getInfo({}))
    // console.log(eos.unsafeRandomKey())
    // this.eos.getAccount('ajksharma23')
  }
}
</script>
