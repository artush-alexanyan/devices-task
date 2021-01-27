<template>
    <b-container fluid class="mt-3 mb-5">
        <b-row>
            <b-col class="col-6">
                <h4 class="text-left mt-3" style="color: black;">
                   <i class="fas fa-angle-left mr-3"></i>
                    Devices
                </h4>
            </b-col>
            <b-col class="col-6">
                <b-button class="btn btn-info float-right mr-5">Create device</b-button>
            </b-col>
        </b-row>
        <b-row>
            <b-col class="col-12 mt-3">
                <b-form-group
                    id="fieldset-1"
                    label-for="input-1"
                    valid-feedback="Thank you!"
                >
                <b-form-input 
                        id="input-1" 
                        placeholder="Search" 
                        v-model="name" trim
                    >
                </b-form-input>
                </b-form-group>                
            </b-col>
        </b-row>
        <b-row>
            <b-col class="col-4">
                <b-form-select></b-form-select>
            </b-col>
            <b-col class="col-4">
                <b-form-select></b-form-select>
            </b-col>
            <b-col class="col-2">
                <b-form-datepicker></b-form-datepicker>
            </b-col>  
            <b-col class="col-2">
                <b-form-datepicker></b-form-datepicker>
            </b-col>                                   
        </b-row>
        <b-row class="mt-3">
            <b-col class="col-4">
                <b-form-select></b-form-select>
            </b-col>
            <b-col class="col-4">
                <b-form-select></b-form-select>
            </b-col>
            <b-col class="col-4">
               
            </b-col>                
        </b-row>
        <b-row class="mt-3">
            <b-col class="col-12">
                <h4 class="text-left ml-3" style="color: black;">Devices</h4>
            </b-col>
            <b-col class="col-12" v-if="!loading">
                  <b-table
                    id="my-table"
                    :items="locations"
                    :per-page="perPage"
                    :current-page="currentPage"
                    small
                    ></b-table> 

                    <b-pagination
                        v-model="currentPage"
                        :total-rows="rows"
                        :per-page="perPage"
                        aria-controls="my-table"
                    ></b-pagination>                                                      
            </b-col>
            <b-col class="col-12" v-else>
                <h6 class="text-center text-secondary mt-5">Loading...</h6>
            </b-col>
        </b-row>
    </b-container>
</template>

<script>
import axios from 'axios'

export default {
    name: 'Rewards',
    data: () => ({
        name: '',
        locations: [],
        perPage: 10,
        currentPage: 1,
        loading: false        
    }),
    computed: {
      rows() {
        return this.locations.length
      }
    },
    methods: {
        getData () {
            this.loading = true
            axios.get('https://portal-api.lurity.com/api/v1/locations',{
                method: "get",
                query: {
                      
                }
            })
            .then(({ data }) => {
                data.data.locations.map((item) => {
                   item.devices.map(it => {
                       this.locations.push({
                           id: it.id,
                           name: it.name,
                           price: `$ ${it.price}`
                       })
                   })
                })
            })
            .then(() => {
                console.log('Success!',)
                this.loading = false
            })         
        }
    },
    created () {
        this.getData()
    }
}
</script>