<template>
    <div v-if="dataReady" id="body-section">
        <div class="s-layout__sidebar">
            <a class="s-sidebar__trigger" href="#0">
                <i class="fa fa-bars"></i>
            </a>
            <!-- actual side bar -->
            <nav class="s-sidebar__nav" style="margin-top:1.3em;">
                <!-- <ScrollPanel style="width: 100%; height: 600px;" class="custom"> -->
                <ul>
                    <h4>Select A User</h4>
                    <li>
                        <MultiSelect
                            v-model="selectedFilterItems.partner_users"
                            :options="filterItems.partner_users"
                            optionLabel="name"
                            display="chip"
                            placeholder="Select a user"
                            style="margin-bottom: 0.7rem"
                            id="select"
                        />
                    </li>
                    <h4>Select Source</h4>
                    <li>
                        <MultiSelect
                            v-model="selectedFilterItems.source"
                            :options="filterItems.source"
                            placeholder="Select Source"
                            display="chip"
                            style="margin-bottom: 0.7rem"
                        />
                    </li>
                    <h4>Select Campaign</h4>
                    <li>
                        <MultiSelect
                            v-model="selectedFilterItems.campaign"
                            :options="filterItems.campaign"
                            placeholder="Select Campaign"
                            display="chip"
                            style="margin-bottom: 0.7rem"
                        />
                    </li>
                    <h4>Select Lenders</h4>
                    <li>
                        <MultiSelect
                            v-model="selectedFilterItems.lenders"
                            :options="filterItems.lenders"
                            optionLabel="lender_name"
                            placeholder="Select a Lender"
                            display="chip"
                            style="margin-bottom: 0.7rem"
                        />
                    </li>
                    <h4>Select Status</h4>
                    <li>
                        <MultiSelect
                            v-model="selectedFilterItems.status"
                            :options="filterItems.status"
                            placeholder="Select a Status"
                            display="chip"
                            style="margin-bottom: 0.7rem"
                        />
                    </li>
                    <h4>Select State</h4>
                    <li>
                        <MultiSelect
                            v-model="selectedFilterItems.state"
                            :options="filterItems.state"
                            placeholder="Select a State"
                            display="chip"
                            style="margin-bottom: 0.7rem"
                        />
                    </li>
                    <h4>Are you a Home Owner?</h4>
                    <li>
                        <MultiSelect
                            v-model="selectedFilterItems.home_owner"
                            :options="filterItems.home_owner"
                            placeholder="Home Ownership"
                            display="chip"
                            style="margin-bottom: 0.7rem"
                        />
                    </li>
                    <!-- <li>
                      <MultiSelect
                        v-model="selectedFilterItems.asset_contract_type"
                        :options="filterItems.asset.contract_type"
                        placeholder="Low Doc v. Full Doc"
                        display="chip"
                        style="margin-bottom: 0.7rem"
                      />
                    </li> -->
                    <!-- this was in the above section @change="storeContractFilter" -->
                    <h4>Select a loan purpose</h4>
                    <li>
                        <MultiSelect
                            v-model="selectedFilterItems.purpose_id"
                            :options="filterItems.purpose"
                            optionLabel="purpose"
                            placeholder="Loan Purpose"
                            display="chip"
                            style="margin-bottom: 0.7rem"
                            id="select"
                        />
                    </li>
                    <li>
                        <h4>Asset type of Equipment</h4>
                        <AssetTree :menuProp="menu"></AssetTree>
                    </li>

                    <li>
                        <h4>Product and Sub Product Type</h4>
                        <ProductTree :menuProductProp="menuProduct"></ProductTree>
                    </li>
                    <br/>
                    <br/>
                    <li>
                        <h4>Loan Amount:$ {{ filterItems.loan_amount }} AUD</h4>
                        <Slider v-model="filterItems.loan_amount" :range="true"/>
                    </li>
                    <br/>
                    <br/>
                    <br/>
                    <li>
                        <h4>Asset Age: {{ filterItems.asset }} years</h4>
                        <Slider v-model="filterItems.asset"/>
                    </li>
                    <br/>
                    <br/>
                    <li>
                        <div class="p-fluid p-grid p-formgrid">
                            <div class="p-field p-col-12 p-md-12">
                                <div class="p-field p-col-12 p-md-12">
                                    <label for="range" style="margin-left: 1em">Date Range</label>
                                    <Calendar
                                        id="range"
                                        v-model="filterItems.start_date"
                                        selectionMode="range"
                                        :manualInput="false"
                                        yearRange="2000:2060"
                                    />
                                </div>
                            </div>
                        </div>
                    </li>
                </ul>
                <!-- </ScrollPanel> -->
            </nav>
        </div>
    </div>
</template>

<script>
import MultiSelect from "primevue/multiselect";

import AssetTree from "./AssetTree.vue";

import ProductTree from "./ProductTree.vue";

import json from "./Newlend.json";

// import ScrollPanel from 'primevue/scrollpanel';

//equipment multi-select
function menu(id, label, children) {
    this.id = id;
    this.label = label;
    this.children = children;
}

//product multi-select
function menuProduct(id, label, children) {
    this.id = id;
    this.label = label;
    this.children = children;
}

export default {
    name: "SideBar",
    components: {MultiSelect, AssetTree, ProductTree},
    data() {
        return {
            // select

            dataReady: false,
            filterItems: null,
            // filterItemsAll: null,
            selectedFilterItems: {},
            chartData: null,

            displayPartnerUsers: [],
            displayLenderName: [],
            // figure this out later
            //init_payload: null,

            // myJson: json,
            menu: [],
            menuProduct: [],
            filter_items: {
                datesRange: null,
                date7: null,
                assetAge: [0, 100],
                loanAmount: [0, 100],
            },
        };
    },
    methods: {
        //api starts
        async initialFilterItemsAndSelectedFilterItems() {
            await axios.get("/dashboard-analytics/init").then((res) => {
                console.log("init-data-here");
                console.log(res);
                // save filter items to vue local data
                this.filterItems = res.data.filter_items;

                console.log("filter-data-here");
                console.log(res.data.filter_items);
                console.log("selected-data-here");
                console.log(res.data.filter_selected);

                // save filter items to vue local data
                this.selectedFilterItems = res.data.filter_selected;
                this.fetchChartData();
            });
            this.dataReady = true;
        },

        fetchChartData() {
            console.log("filterdata");
            console.log(this.init_payload);

            // user id
            let partner_users = this.selectedFilterItems.partner_users;
            let partner_user_id = this.mapToNumber(partner_users); // [1,2,3..]
            this.selectedFilterItems.partner_user_id = partner_user_id

            // lender id
            let lenders = this.selectedFilterItems.lenders;
            let lender_id = this.mapToNumber(lenders); // [1,2,3..]
            this.selectedFilterItems.lender_id = lender_id


            axios.post("/dashboard-analytics/run", this.selectedFilterItems).then(
                (res) => {
                    // let data = res.data or res.data.data
                    console.log("post-payload-data");
                    console.log(res);
                    // save data to vue local data
                    this.chartData = res.data.data;
                },
                (error) => {
                    console.log(error);
                }
            );
        },

        handleFilterChange() {
            this.fetchChartData();
        },

        handleFilterChangeMock() {
            alert("refetch data with new filter, chart data should be updated");
            this.fetchChartDataMock();
        },
        // mapping purpose objects
        mapToPurposeObjs(purposeIds, purposes) {

            let mapped

        },


        //mapping lender objects
        mapToLenderObjs(lenderIds, lenders) {
            let mapped = lenderIds.map((id, index) => {
                let foundIndex = lenders.findIndex(
                    lender => lender.lender_id == lenderIds[index]
                );
                let foundLender = lenders[foundIndex];
                console.log("lender-data");
                console.log(foundLender);
                console.log(lenderIds[index]);
                return {
                    "lender_id": lenderIds[index],
                    "lender_name": foundLender.lender_name,
                };
            });
            console.log(mapped);
            return mapped;
        },
        //mapping user objects
        mapToObjects(userIds, users) {
            let emptyArray = [];

            for (let i = 0; i < userIds.length; i++) {
                let foundIndex = users.findIndex(
                    (user) => user.partner_user_id == userIds[i]
                );
                let foundUser = users[foundIndex];

                let user = {
                    partner_user_id: userIds[i],
                    name: foundUser.name,
                };

                emptyArray.push(user);
            }
            console.log("user-data");
            console.log(emptyArray);
            return emptyArray;
        },
        //convering user object back to number
        mapToNumber(userWithNameAndId) {
            let mapped = userWithNameAndId.map((userObject) => {
                return userObject.partner_user_id;
            });
            console.log(mapped);
            return mapped;
        },
    },
    beforeMount() {
        //this.getProductType(),
        //this.gethis(),
        //this.initialFilterItemsAndSelectedFilterItems();
        //this.dataReady = true;
    },
    async mounted() {
        await this.initialFilterItemsAndSelectedFilterItems();

        //prep for mapping user object
        let userIds = this.selectedFilterItems.partner_user_id;
        let users = this.filterItems.partner_users;
        //console.log("user-data-here");
        //console.log(userIds);
        //console.log(users);
        let userWithNameAndId = this.mapToObjects(userIds, users);
        this.selectedFilterItems.partner_users = userWithNameAndId
        delete this.selectedFilterItems.partner_user_id
        // this.displayPartnerUsers = userWithNameAndId;
        this.mapToNumber(userWithNameAndId);

        // prep for mapping lender object
        let lenderIds = this.selectedFilterItems.lender_id;
        let lenders = this.filterItems.lenders;
        //console.log("lender-data-here");
        //console.log(lenderIds);
        //console.log(lenders);
        let lenderWithNameAndId = this.mapToLenderObjs(lenderIds, lenders);
        console.log(lenderWithNameAndId);
        this.selectedFilterItems.lenders = lenderWithNameAndId
        delete this.selectedFilterItems.lender_id
        // this.displayLenderName = lenderWithNameAndId;

        //prep for mapping loan purpose
        let purposeIds = this.selectedFilterItems.purpose_id;
        let purposes = this.filterItems.purpose;
        console.log('purpose-data-here');
        console.log(purposeIds);
        console.log(purposes);
    },

    //api ends

    gethis() {
        console.log("HIIII");
        var p = this.myJson.filter_items.industries;
        //var p = this.filterItems.industries
        //console.log(p)
        //console.log(p)
        var industries = [];
        for (var key of Object.keys(p)) {
            industries.push(p[key]);
            // for (var inside of key){
            //      //console.log(inside);
            // }
        }

        var multiselect = [];
        for (var key in industries) {
            var item = new menu();
            var children = [];
            for (var key2 in industries[key].children) {
                children.push({
                    id:
                        industries[key].children[key2].child +
                        "-" +
                        industries[key].parent.child,
                    label: industries[key].children[key2].child,
                });
            }
            item.children = children;
            for (var key2 in industries[key].parent) {
                item.id = industries[key].parent.child;
                item.label = industries[key].parent.child;
                //console.log(industries[key].parent.child)
            }
            multiselect.push(item);
        }
        this.menu = multiselect;
    },

    getProductType() {
        var pro = this.myJson.filter_items.product_types;

        // get product object
        var productTypes = [];
        for (var key2 of Object.keys(pro)) {
            //  console.log(pro[key]);
            // console.log('hi');
            productTypes.push(pro[key2]);
        }

        // get data to align with multiselect format
        var multiselectProduct = [];
        for (var key in productTypes) {
            var item = new menuProduct();
            var children = [];

            for (var key2 in productTypes[key].sub_products) {
                // console.log('hi');
                //console.log(productTypes[key].sub_products[key2].product_type_name);
                children.push({
                    id: productTypes[key].sub_products[key2].product_type_name,
                    label: productTypes[key].sub_products[key2].product_type_name,
                });
            }
            //console.log(children);
            item.children = children;
            //console.log(subProduct);
            for (var key3 in productTypes[key]) {
                //console.log(productTypes[key]);
                item.id = productTypes[key].product_type_name;
                item.label = productTypes[key].product_type_name;
            }
            multiselectProduct.push(item);
            //console.log(multiselectProduct);
        }
        this.menuProduct = multiselectProduct;
        console.log(this.menuProduct);
    },
    onSelectAllChange(event) {
        this.selectedItems = event.checked
            ? this.items.map((item) => item.value)
            : [];
        this.selectAll = event.checked;
    },
    onChange(event) {
        this.selectAll = event.value.length === this.items.length;
    },
    created() {
        //this.selectedCategory = this.categories[1];
        //date range
        let today = new Date();
        let month = today.getMonth();
        let year = today.getFullYear();
        let prevMonth = month === 0 ? 11 : month - 1;
        let prevYear = prevMonth === 11 ? year - 1 : year;
        let nextMonth = month === 11 ? 0 : month + 1;
        let nextYear = nextMonth === 0 ? year + 1 : year;
        this.minDate = new Date();
        this.minDate.setMonth(prevMonth);
        this.minDate.setFullYear(prevYear);
        this.maxDate = new Date();
        this.maxDate.setMonth(nextMonth);
        this.maxDate.setFullYear(nextYear);

        let invalidDate = new Date();
        invalidDate.setDate(today.getDate() - 1);
        this.invalidDates = [today, invalidDate];
    },
};
</script>

<style>
.p-component {
    font-size: 1.1em !important;
}

.p-multiselect-panel .p-multiselect-items {
    margin-top: 9px;
    padding: 0;
}

.p-multiselect.p-multiselect-label {
    padding: 0.9rem !important;
    color: #474747 !important;
}

.vue-treeselect__control {
    width: 28rem;
}

.p-multiselect.p-component.p-inputwrapper {
    border: none;
}

.p-multiselect .p-multiselect-label.p-placeholder {
    color: #474747 !important;
    padding: 0.7rem;
}

h4 {
    margin-left: 1.2em;
    margin-right: -3em;
    color: #474747;
}

h3 {
    margin-inline-start: 0.5em;
}

.p-slider.p-slider-horizontal {
    margin-inline-start: 1em;
}

.p-slider .p-slider-range {
    background: #304ff8;
}

.p-slider {
    background: #474747;
}

.p-multiselect {
    width: 28rem;
}

.p-multiselect-panel .p-multiselect-items .p-multiselect-item {
    top: 5px;
    background: white !important;
    width: 21em;
}

/* Primary Styles */
*,
*::before,
*::after {
    box-sizing: border-box;
    /* background-color: white; */
}

/* actual sidebar */
.s-sidebar__nav {
    position: absolute;
    top: 0;
    left: -26em;
    overflow: hidden;
    transition: all 0.3s ease-in;
    width: 26em;
    height: 100%;
    background-color: #00c883;
    box-shadow: 3px 0px 4px 1px rgba(0, 0, 0, 0.1);
    z-index: 0;
}

/*
.s-sidebar__nav:hover,
.s-sidebar__nav:focus,
.s-sidebar__trigger:focus + .s-sidebar__nav,
.s-sidebar__trigger:hover + .s-sidebar__nav {
  left: 0;
} */

.s-sidebar__nav ul {
    position: absolute;
    top: 0em;
    left: 0em;
    margin: 0;
    padding: 0;
    width: 15em;
}

.s-sidebar__nav ul li {
    width: 100%;
}

/* Mobile First */
@media (min-width: 42em) {
    .s-sidebar__nav {
        width: 0em;
        left: 1em;
    }

    .s-sidebar__nav:hover,
    .s-sidebar__nav:focus,
    .s-sidebar__trigger:hover + .s-sidebar__nav,
    .s-sidebar__trigger:focus + .s-sidebar__nav {
        width: 26em;
    }
}

@media (min-width: 48em) {
    .s-layout__content {
        margin-left: 26em;
    }

    /* Sidebar */
    .s-sidebar__trigger {
        display: none;
    }

    .s-sidebar__nav {
        width: 26em;
    }

    .s-sidebar__nav ul {
        top: 1.3em;
        left: 1.3em;
    }
}
</style>
