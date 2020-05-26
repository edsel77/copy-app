<template>
  <div class="col-lg-4 col-md-6 col-sm-8">
    <b-form>
      <b-form-group
        id="input-group-1"
        label="Data 1:"
        label-for="input-1"
      >
        <b-form-input
          id="input-1"
          v-model="form.data1"
          type="text"
          required
          placeholder="Data 1"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-2" label="Data 2:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="form.data2"
          required
          placeholder="Data 2"
        ></b-form-input>
      </b-form-group>

      <b-button type="button" variant="primary" @click="doCopy">Copy</b-button>
    </b-form>
  </div>
</template>

<script>
export default {
    name: 'Form',
    data(){
        return {
            form: {
                data1: '',
                data2: '',
            },
        }
    },
    methods: {
      doCopy: function () {
        let clip = '';
        let key_formats = {
            'data1': 'Data 1',
            'data2': 'Data 2',
        }
        
        for (var key in this.form) {
            if (this.form.hasOwnProperty(key)) {
                Object.entries(key_formats).forEach(([key_format, val]) => {
                    if(key_format == key) clip += val + ': ' + this.form[key] + '\n';
                });
            }
        }
        this.$copyText(clip).then(function (e) {
            Swal.fire(
              'Success!',
              'Successfully copied.',
              'success'
            )
        }, function (e) {
            Swal.fire(
              'Error!',
              'Error on copy, please try again.',
              'error'
            )
        })
      }
    }
}
</script>