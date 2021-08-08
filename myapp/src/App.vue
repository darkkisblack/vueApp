<template>
    <div id="app-container">
        <DxDataGrid
            :data-source="employees"
            key-expr="EmployeeID"
             :allow-column-resizing="true"
             :column-auto-width="true"
             :allow-column-reordering="true">
            <DxColumn data-field="FullName"></DxColumn>
            <DxColumn data-field="Position"></DxColumn>
            <DxColumn
                data-field="BirthDate"
                data-type="date">
            </DxColumn>
            <DxColumn
                data-field="HireDate"
                data-type="date">
            </DxColumn>
            <DxColumn data-field="City" />
             <DxColumn
              data-field="Country"
              :group-index="0"
               sort-order="asc">
        <DxRequiredRule />
      </DxColumn>
            <DxGroupPanel :visible="true" />
            <DxColumn data-field="Address" />
            <DxColumn data-field="HomePhone" />
            <DxColumn data-field="PostalCode" />
             <DxFilterRow :visible="true" />
             <DxSearchPanel :visible="true" />
             <DxEditing
                mode="popup"
                :allow-updating="true"
                :allow-adding="true"
                :allow-deleting="true"/>
                <DxSelection mode="single"/>
                 <DxMasterDetail
                 :enabled="true"
                  template="employee-info"/>
               <template #employee-info="{ data: employee }">
                <div>
                 <img class="employee-photo" :src="employee.data.Photo">
                 <p class="employee-notes">{{ employee.data.Notes }}</p>
                </div>
                </template>
        </DxDataGrid>
    </div>
</template>

<script>
import {
  DxDataGrid,
  DxColumn,
  DxFilterRow,
  DxSearchPanel,
  DxEditing,
  DxSelection,
  DxMasterDetail,
} from 'devextreme-vue/data-grid';
import service from './employees.service';

export default {
  name: 'App',
  components: {
    DxDataGrid,
    DxColumn,
    DxFilterRow,
    DxSearchPanel,
    DxEditing,
    DxSelection,
    DxMasterDetail,
  },
  // ...
  data() {
    return {
      employees: service.getEmployees(),
    };
  },
};
</script>

<style>
#dataGrid {
    height: 500px;
}
.employee-photo {
    height: 140px;
    float: left;
    padding: 0 20px 20px 0;
}

.employee-notes {
    text-align: justify;
    white-space: normal;
}
</style>
