<template>
<div>
  <div class="panel-body">
    <vue-form-generator :schema="schema" :model="model" :options="formOptions"></vue-form-generator>
  </div>
  <h1>
  Description
  </h1>
  <span v-html = "model.description" />
  </div>
</template>

<script>
import Vue from 'vue'
import VueFormGenerator from 'vue-form-generator'
import 'vue-form-generator/dist/vfg.css'

Vue.use(VueFormGenerator)


export default {
  name: 'HelloWorld',
  methods: {
    submit:function(event){
      console.log('foo');
    }
  },
  data () {
    return {
      model: {
        mounts:[]
      },
      schema: {
        fields: [
          {
            type: 'input',
            inputType: 'text',
            label: 'Globally Unique ID',
            model: 'id',
            value:Math.floor(Math.random() * 1000000),
          },
          {
            type: 'input',
            inputType: 'text',
            label: 'Source (ID of Associated Manufacturer)',
            model: 'source',
            placeholder: 'Your name',
            featured: true,
          },
          {
            type: 'input',
            inputType: 'text',
            label: 'Name (Frame and License Name)',
            model: 'name',
            validator: VueFormGenerator.validators.string
          },
          {
            type: 'input',
            inputType:'text',
            label: 'Mech Type',
            model: 'mechType',
          },
          {
            type: 'textArea',
            label: 'Description (supports HTML Markdown)',
            model: 'description',
          },
        ],
        groups:[
          { legend:'Mounts',
          fields:[
            {
            type: 'input',
            inputType:'number',
            label: 'Heavy Mount',
            min:0,
            model: 'heavyMount',
          },
          {
            type: 'input',
            inputType:'number',
            label: 'Main',
            min:0,
            model: 'mainMount',
          },
          {
            type: 'input',
            inputType:'number',
            label: 'Main/Aux',
            min:0,
            model: 'mainAuxMount',
          },
          {
            type: 'input',
            inputType:'number',
            label: 'Aux',
            min:0,
            model: 'auxMount',
          },
          {
            type: 'input',
            inputType:'number',
            label: 'Aux/Aux',
            min:0,
            model: 'auxAuxMount',
          },
          {
            type: 'input',
            inputType:'number',
            label: 'Flex',
            min:0,
          },
          {
            type:'submit',
            label:'Submit',
            onSubmit:function(model){

              var foo = JSON.stringify(model)
              console.log(foo);
            }
          }
        ]
      }
        ]
      },
      formOptions: {
        validateAfterLoad: true,
        validateAfterChanged: true,
        validateAsync: true
      }
    }
  }
}
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
