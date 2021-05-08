<template>
  <div class="rajkot">
      <b-table
            :data="hospitals"
            :bordered="false"
            :striped="true"
            :narrowed="false"
            :hoverable="false"
            :loading="false"
            :focusable="false"
            :mobile-cards="true">
        <b-table-column field="name" label="Hospital" width="40" :td-attrs="columnTdAttrs"
        numeric v-slot="props">
          {{ props.row.name }}
        </b-table-column>
        <b-table-column field="name" label="Hospital Type" width="40"
        :td-attrs="columnTdAttrs" numeric v-slot="props">
          {{ props.row.type }}
        </b-table-column>
        <b-table-column field="name" label="Address" width="40" :td-attrs="columnTdAttrs"
        numeric v-slot="props">
          {{ props.row.address }}
        </b-table-column>
        <b-table-column field="name" label="Total Normal Beds" width="40"
        :td-attrs="columnTdAttrs" numeric v-slot="props">
          {{ props.row.total_normal_beds }}
        </b-table-column>
        <b-table-column field="name" label="Available Normal Beds" width="40"
        :td-attrs="columnTdAttrs" numeric v-slot="props">
          {{ props.row.normal_beds_available }}
        </b-table-column>
        <b-table-column field="name" label="Total Ventilator Beds" width="40"
        :td-attrs="columnTdAttrs" numeric v-slot="props">
          {{ props.row.total_beds_with_ventilator }}
        </b-table-column>
        <b-table-column field="name" label="Available Ventilator Beds" width="40"
        :td-attrs="columnTdAttrs" numeric v-slot="props">
          {{ props.row.ventilator_beds_available }}
        </b-table-column>
        <b-table-column field="name" label="Total ICU Beds" width="40"
        :td-attrs="columnTdAttrs" numeric v-slot="props">
          {{ props.row.total_icu_beds }}
        </b-table-column>
        <b-table-column field="name" label="Available ICU Beds" width="40"
        :td-attrs="columnTdAttrs" numeric v-slot="props">
          {{ props.row.icu_beds_available }}
        </b-table-column>
        <b-table-column field="name" label="Fire Safety Compliance" width="40"
        :td-attrs="columnTdAttrs" numeric v-slot="props">
          {{ props.row.fire_safety_compliance }}
        </b-table-column>
        <b-table-column field="name" label="Hospital Contact No." width="40"
        :td-attrs="columnTdAttrs" v-slot="props">
          {{ props.row.hospital_contact_number }}
        </b-table-column>
        <b-table-column field="name" label="Contact Person Name" width="40"
        :td-attrs="columnTdAttrs" numeric v-slot="props">
          {{ props.row.contact_person_name }}
        </b-table-column>
        <b-table-column field="name" label="Contact Person Mobile" width="40"
        :td-attrs="columnTdAttrs" numeric v-slot="props">
          {{ props.row.contact_person_mobile }}
        </b-table-column>
        <b-table-column field="name" label="Liason Officer Mobile" width="40"
        :td-attrs="columnTdAttrs" numeric v-slot="props">
          {{ props.row.liason_officer_phone }}
        </b-table-column>
      </b-table>
  </div>
</template>

<script lang='ts'>

import axios from 'axios';
/* eslint-disable */
export default {
  name: 'HelloWorld',
  created() {
    axios.get('https://immense-refuge-93264.herokuapp.com/hospitals/')
    .then((result) => {
        console.log(result.data);
        console.log(this);
        (this as any).hospitals = result.data;
      })
      .catch((error) => {
        console.log(error);
        });
      },
  methods: {
    columnTdAttrs(row: any, column: any) {
      let retobj = null;
            if (row.id === 'Total') {
                if (column.label === 'Hospital') {
                    retobj = {
                        colspan: 4,
                        class: 'has-text-weight-bold',
                        style: {
                            'text-align': 'left !important',
                        },
                    };
                } else {
                    retobj = {
                        style: { display: 'none' },
                    };
                }
            }
            return retobj;
        },
  },
  data() {
    return {
      hospitals: [],
    };
  },
};
</script>

<style>
.rajkot {
  align-content: center;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
