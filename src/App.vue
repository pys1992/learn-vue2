<template>
    <div id="app">
        <select v-model="selectedFilterItems.partner_user_id" @change="handleFilterChangeMock">
            <option v-for="(partner_user,index) in filterItems.partner_users"
                    :key="index"
                    :value="partner_user.partner_user_id">
                {{ partner_user.name }}
            </option>
        </select>

        <div>
            <h2>chart</h2>
            <div>{{ chartData.single_figures.loan_book }}</div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            filterItems: null,
            selectedFilterItems: null,
            chartData: null
        }
    },

    mounted() {
        // this.initialFilterItemsAndSelectedFilterItems()
        this.initialFilterItemsAndSelectedFilterItemsMock()
    },

    methods: {
        initialFilterItemsAndSelectedFilterItems() {
            axios.get('/init').then(res => {

                // save filter items to vue local data
                this.filterItems = res.data.filter_items; // maybe res.data.data.filter_items

                // save filter items to vue local data
                this.selectedFilterItems = res.data.filter_selected; // maybe res.data.data.filter_selected

                // then fetch chart data with full filters
                this.fetchChartData();
            })
        },

        fetchChartData() {
            axios.psot('/run', this.selectedFilterItems).then(res => {
                // let data = res.data or res.data.data

                // save data to vue local data
                this.chartData = responseData
            })
        },

        handleFilterChange() {
            this.fetchChartData()
        },

        initialFilterItemsAndSelectedFilterItemsMock() {
            this.filterItems = {
                "partner_users": [
                    {
                        "partner_user_id": "418",
                        "name": "Robert Trevarrow "
                    },
                    {
                        "partner_user_id": "801",
                        "name": "Gary"
                    },
                    {
                        "partner_user_id": "814",
                        "name": "Nick Bluhdorn"
                    },
                    {
                        "partner_user_id": "859",
                        "name": "Erin Bluhdorn"
                    },
                    {
                        "partner_user_id": "923",
                        "name": "Eric Leao"
                    },
                    {
                        "partner_user_id": "925",
                        "name": "Luke Howe"
                    },
                    {
                        "partner_user_id": "961",
                        "name": "David Crook"
                    }
                ],
                "source": [
                    "APP",
                    "LeanApp",
                    "PartnerAPI",
                    "Partners"
                ],
                "campaign": [
                    "awler18",
                    "awler23",
                    "awler5",
                    "BFJan",
                    "projv19",
                    "projv20",
                    "projv21"
                ],
                "lenders": [
                    {
                        "lender_id": "1",
                        "lender_name": "Capify Australia"
                    },
                    {
                        "lender_id": "3",
                        "lender_name": "GetCapital"
                    },
                    {
                        "lender_id": "5",
                        "lender_name": "Prospa"
                    },
                    {
                        "lender_id": "6",
                        "lender_name": "Business Fuel"
                    },
                    {
                        "lender_id": "7",
                        "lender_name": "Max Funding"
                    },
                    {
                        "lender_id": "8",
                        "lender_name": "OnDeck Australia"
                    },
                    {
                        "lender_id": "9",
                        "lender_name": "Moula"
                    },
                    {
                        "lender_id": "10",
                        "lender_name": "Lumi"
                    },
                    {
                        "lender_id": "14",
                        "lender_name": "Bizcap"
                    },
                    {
                        "lender_id": "15",
                        "lender_name": "Equipment"
                    },
                    {
                        "lender_id": "17",
                        "lender_name": "Limba Loans"
                    },
                    {
                        "lender_id": "18",
                        "lender_name": "ABR Finance Pty Ltd"
                    },
                    {
                        "lender_id": "19",
                        "lender_name": "HomeSec"
                    },
                    {
                        "lender_id": "20",
                        "lender_name": "Strive Financial"
                    },
                    {
                        "lender_id": "23",
                        "lender_name": "Your Manager"
                    },
                    {
                        "lender_id": "24",
                        "lender_name": "Lend Assisted"
                    },
                    {
                        "lender_id": "25",
                        "lender_name": "Finance One"
                    },
                    {
                        "lender_id": "26",
                        "lender_name": "ScotPac Business Finance"
                    },
                    {
                        "lender_id": "27",
                        "lender_name": "Invoice Money"
                    },
                    {
                        "lender_id": "33",
                        "lender_name": "Banjo Loans"
                    },
                    {
                        "lender_id": "35",
                        "lender_name": "Speedy Finance"
                    },
                    {
                        "lender_id": "36",
                        "lender_name": "Fuzion Capital"
                    },
                    {
                        "lender_id": "41",
                        "lender_name": "TradePlus24 Australia Pty Ltd"
                    },
                    {
                        "lender_id": "47",
                        "lender_name": "Funda Business Finance"
                    },
                    {
                        "lender_id": "48",
                        "lender_name": "Earlypay"
                    },
                    {
                        "lender_id": "54",
                        "lender_name": "Funding"
                    },
                    {
                        "lender_id": "56",
                        "lender_name": "APositive Pty Ltd"
                    },
                    {
                        "lender_id": "59",
                        "lender_name": "Butn Co"
                    },
                    {
                        "lender_id": "61",
                        "lender_name": "Interim Finance "
                    },
                    {
                        "lender_id": "63",
                        "lender_name": "Finport Finance Pty Ltd"
                    },
                    {
                        "lender_id": "64",
                        "lender_name": "In Front Australian Business Solutions Pty Ltd"
                    },
                    {
                        "lender_id": "67",
                        "lender_name": "Demo "
                    },
                    {
                        "lender_id": "69",
                        "lender_name": "Fifo Capital Australia Pty Ltd"
                    },
                    {
                        "lender_id": "70",
                        "lender_name": "Octet Finance Pty Ltd "
                    },
                    {
                        "lender_id": "71",
                        "lender_name": "Australian Secure Capital Fund Ltd."
                    },
                    {
                        "lender_id": "72",
                        "lender_name": "Seascape (2010) Limited"
                    },
                    {
                        "lender_id": "73",
                        "lender_name": "Moneytech Finance Pty Ltd"
                    },
                    {
                        "lender_id": "74",
                        "lender_name": "ScotPac Asset Finance"
                    },
                    {
                        "lender_id": "76",
                        "lender_name": "Grow Finance Group Pty Ltd"
                    },
                    {
                        "lender_id": "77",
                        "lender_name": "Nova Cash Flow Finance Pty Ltd"
                    },
                    {
                        "lender_id": "78",
                        "lender_name": "Finstro"
                    },
                    {
                        "lender_id": "81",
                        "lender_name": "Lend Asset Assist"
                    },
                    {
                        "lender_id": "82",
                        "lender_name": "Revas Mortgage Management"
                    },
                    {
                        "lender_id": "83",
                        "lender_name": "Group And General Finance Pty Ltd"
                    },
                    {
                        "lender_id": "84",
                        "lender_name": "Drive Finance Solution"
                    },
                    {
                        "lender_id": "85",
                        "lender_name": "Asset Finance Shop"
                    },
                    {
                        "lender_id": "86",
                        "lender_name": "Fleet Partners"
                    },
                    {
                        "lender_id": "87",
                        "lender_name": "EarlyPay Equipment"
                    },
                    {
                        "lender_id": "88",
                        "lender_name": "MorrisFinance"
                    },
                    {
                        "lender_id": "89",
                        "lender_name": "CSA Private Mortgages"
                    },
                    {
                        "lender_id": "90",
                        "lender_name": "Eastwood Securities Pty Ltd"
                    },
                    {
                        "lender_id": "92",
                        "lender_name": "Zip Business"
                    },
                    {
                        "lender_id": "93",
                        "lender_name": "Tradies Finance"
                    },
                    {
                        "lender_id": "94",
                        "lender_name": "Equifund Financial Group"
                    }
                ],
                "status": [
                    "Attempting",
                    "In Progress",
                    "Pending",
                    "Rejected",
                    "Settled"
                ],
                "product_types": [
                    {
                        "product_type_id": "1",
                        "product_type_name": "Unsecured Loan",
                        "product_icon": "products/unsecured_loan",
                        "description": "A business loan that is not secured. Typically lenders will lend up to 100% of your clients monthly sales.",
                        "active": "1",
                        "sub_product": "0",
                        "sub_products": []
                    },
                    {
                        "product_type_id": "2",
                        "product_type_name": "Secured Loan",
                        "product_icon": "products/secured_loan",
                        "description": "A business loan that is secured with either property, vehicle or equipment to strengthen your clients application.",
                        "active": "1",
                        "sub_product": "0",
                        "sub_products": []
                    },
                    {
                        "product_type_id": "3",
                        "product_type_name": "Line of Credit",
                        "product_icon": "products/line_of_credit",
                        "description": "A revolving line of credit facility. As long as the balance is below the approved limit, the client can redraw at any time for any business purpose.",
                        "active": "1",
                        "sub_product": "0",
                        "sub_products": []
                    },
                    {
                        "product_type_id": "4",
                        "product_type_name": "Overdraft Facility",
                        "product_icon": "products/overdraft_facility",
                        "description": "A bankless business overdraft, securely linked to any transaction account.",
                        "active": "1",
                        "sub_product": "0",
                        "sub_products": []
                    },
                    {
                        "product_type_id": "6",
                        "product_type_name": "SMSF",
                        "product_icon": "products/commercial_smsf",
                        "description": "Funds are used by a self-managed super fund to purchase property.",
                        "active": "1",
                        "sub_product": "0",
                        "sub_products": []
                    },
                    {
                        "product_type_id": "7",
                        "product_type_name": "Private Lending",
                        "product_icon": "products/caveat_loan",
                        "description": "By using their property as security the client can access funds for business purposes. Lenders have varying LVR's which will determine the lending amount.",
                        "active": "1",
                        "sub_product": "0",
                        "sub_products": [
                            {
                                "product_type_id": "15",
                                "product_type_name": "Bridging",
                                "product_icon": "products/caveat_loan",
                                "description": null,
                                "active": "1",
                                "sub_product": "7"
                            },
                            {
                                "product_type_id": "16",
                                "product_type_name": "Term Loan",
                                "product_icon": "products/caveat_loan",
                                "description": null,
                                "active": "1",
                                "sub_product": "7"
                            },
                            {
                                "product_type_id": "17",
                                "product_type_name": "Capitalised Interest",
                                "product_icon": "products/caveat_loan",
                                "description": null,
                                "active": "1",
                                "sub_product": "7"
                            },
                            {
                                "product_type_id": "18",
                                "product_type_name": "Interest Only",
                                "product_icon": "products/caveat_loan",
                                "description": null,
                                "active": "1",
                                "sub_product": "7"
                            }
                        ]
                    },
                    {
                        "product_type_id": "8",
                        "product_type_name": "Invoice Finance",
                        "product_icon": "products/invoice_factoring",
                        "description": "Gain access to funds for your clients with a true invoice factoring product. We even have single invoice providers.",
                        "active": "1",
                        "sub_product": "0",
                        "sub_products": []
                    },
                    {
                        "product_type_id": "9",
                        "product_type_name": "Merchant Cash Advance",
                        "product_icon": "products/merchant_cash_advance",
                        "description": "Rather than fixed daily repayments, a small percentage of credit card and EFTPOS terminal sales is repaid daily for the term of the Cash Advance.",
                        "active": "1",
                        "sub_product": "0",
                        "sub_products": []
                    },
                    {
                        "product_type_id": "10",
                        "product_type_name": "Asset Finance",
                        "product_icon": "products/equipment_finance",
                        "description": "Finance your clients equipment with a range of lenders offering great rates across vehicle, office equipment and yellow goods.",
                        "active": "1",
                        "sub_product": "0",
                        "sub_products": [
                            {
                                "product_type_id": "20",
                                "product_type_name": "Chattel Mortgage",
                                "product_icon": "products/equipment_finance",
                                "description": null,
                                "active": "1",
                                "sub_product": "10"
                            },
                            {
                                "product_type_id": "21",
                                "product_type_name": "Finance Lease",
                                "product_icon": "products/equipment_finance",
                                "description": null,
                                "active": "1",
                                "sub_product": "10"
                            },
                            {
                                "product_type_id": "23",
                                "product_type_name": "Operating Lease",
                                "product_icon": "products/equipment_finance",
                                "description": "Fully Maintained Operating Lease for motor vehicles allows users to pay a single monthly rental covering all running costs and simply return the vehicle at the end of an agreed term.",
                                "active": "1",
                                "sub_product": "10"
                            }
                        ]
                    },
                    {
                        "product_type_id": "11",
                        "product_type_name": "Other / Not Sure",
                        "product_icon": "products/other",
                        "description": "Select this for everything else, or if you're not sure.",
                        "active": "1",
                        "sub_product": "0",
                        "sub_products": []
                    },
                    {
                        "product_type_id": "14",
                        "product_type_name": "Combination / Multiple",
                        "product_icon": "products/invoice_factoring",
                        "description": "When your client requires funds for multiple purposes - i.e $20k for a new truck, $10k for cashflow, $15k for tax debt.",
                        "active": "1",
                        "sub_product": "0",
                        "sub_products": []
                    },
                    {
                        "product_type_id": "19",
                        "product_type_name": "Trade Finance",
                        "product_icon": null,
                        "description": "Trade finance can be used to pay domestic and international suppliers. A trade transaction requires a seller of goods and services as well as a buyer. Typically, the lender will pay the the seller when the goods are shipped and provide credit to your client.",
                        "active": "1",
                        "sub_product": "0",
                        "sub_products": []
                    },
                    {
                        "product_type_id": "24",
                        "product_type_name": "Construction Funding",
                        "product_icon": "products/construction_funding",
                        "description": "Funds for multi-unit developments, land sub-divisions, caravan parks, industrial property development or major renovations.",
                        "active": "1",
                        "sub_product": "0",
                        "sub_products": []
                    }
                ],
                "purpose": [
                    {
                        "purpose_id": "1",
                        "purpose": "Working Capital"
                    },
                    {
                        "purpose_id": "2",
                        "purpose": "Inventory"
                    },
                    {
                        "purpose_id": "3",
                        "purpose": "Equipment"
                    },
                    {
                        "purpose_id": "4",
                        "purpose": "Renovation"
                    },
                    {
                        "purpose_id": "5",
                        "purpose": "Unexpected Expenses"
                    },
                    {
                        "purpose_id": "6",
                        "purpose": "Hiring Staff"
                    },
                    {
                        "purpose_id": "7",
                        "purpose": "Tax"
                    },
                    {
                        "purpose_id": "9",
                        "purpose": "To Start a New Business"
                    },
                    {
                        "purpose_id": "10",
                        "purpose": "Purchase Existing Business"
                    },
                    {
                        "purpose_id": "11",
                        "purpose": "Expansion"
                    },
                    {
                        "purpose_id": "8",
                        "purpose": "Other"
                    }
                ],
                "state": [
                    "ACT",
                    "NSW",
                    "VIC",
                    "QLD",
                    "SA",
                    "WA",
                    "TAS",
                    "NT"
                ],
                "industries": [
                    {
                        "parent": {
                            "industry_id": "52",
                            "parent": null,
                            "child": "Arts & Lifestyle",
                            "tree": "Arts & Lifestyle >> ",
                            "thesaurus": null
                        },
                        "children": [
                            {
                                "industry_id": "53",
                                "parent": "52",
                                "child": "Health & Fitness Centres, Gyms",
                                "tree": "Arts & Lifestyle >> Health & Fitness Centres, Gyms",
                                "thesaurus": "fitness, trainer, pt, personal trainer"
                            },
                            {
                                "industry_id": "54",
                                "parent": "52",
                                "child": "Movie, Film & Video Services",
                                "tree": "Arts & Lifestyle >> Movie, Film & Video Services",
                                "thesaurus": "camera, sound, production"
                            },
                            {
                                "industry_id": "55",
                                "parent": "52",
                                "child": "Parks & Gardens",
                                "tree": "Arts & Lifestyle >> Parks & Gardens",
                                "thesaurus": "recreation"
                            },
                            {
                                "industry_id": "56",
                                "parent": "52",
                                "child": "Photographic Services",
                                "tree": "Arts & Lifestyle >> Photographic Services",
                                "thesaurus": "camera, photography, photographer, film, media"
                            },
                            {
                                "industry_id": "57",
                                "parent": "52",
                                "child": "Radio & TV Services",
                                "tree": "Arts & Lifestyle >> Radio & TV Services",
                                "thesaurus": "media, television, production, film, movie, studio"
                            },
                            {
                                "industry_id": "58",
                                "parent": "52",
                                "child": "Religious Organisations",
                                "tree": "Arts & Lifestyle >> Religious Organisations",
                                "thesaurus": "church"
                            },
                            {
                                "industry_id": "59",
                                "parent": "52",
                                "child": "Services to the Arts",
                                "tree": "Arts & Lifestyle >> Services to the Arts",
                                "thesaurus": "studio"
                            },
                            {
                                "industry_id": "60",
                                "parent": "52",
                                "child": "Sports & Physical Recreation",
                                "tree": "Arts & Lifestyle >> Sports & Physical Recreation",
                                "thesaurus": "trainer, pt, personal trainer"
                            },
                            {
                                "industry_id": "61",
                                "parent": "52",
                                "child": "Other",
                                "tree": "Arts & Lifestyle >> Other",
                                "thesaurus": "fine art, artist, design"
                            }
                        ]
                    },
                    {
                        "parent": {
                            "industry_id": "62",
                            "parent": null,
                            "child": "Construction & Trades",
                            "tree": "Construction & Trades >> ",
                            "thesaurus": null
                        },
                        "children": [
                            {
                                "industry_id": "63",
                                "parent": "62",
                                "child": "Air Con, Heating, Solar Services",
                                "tree": "Construction & Trades >> Air Con, Heating, Solar Services",
                                "thesaurus": "cooling, refrigeration, conditioning"
                            },
                            {
                                "industry_id": "64",
                                "parent": "62",
                                "child": "Bricklaying",
                                "tree": "Construction & Trades >> Bricklaying",
                                "thesaurus": "brickie, brick, bricklayer, labourer"
                            },
                            {
                                "industry_id": "65",
                                "parent": "62",
                                "child": "Building Construction",
                                "tree": "Construction & Trades >> Building Construction",
                                "thesaurus": "tradie, builder, labourer, worker, craftsman, craftsperson, tradesman, master builder"
                            },
                            {
                                "industry_id": "66",
                                "parent": "62",
                                "child": "Carpentry",
                                "tree": "Construction & Trades >> Carpentry",
                                "thesaurus": "chippy, carpenter, carpentry, cabinet maker, builder, joiner, woodworker, cabinetmaker, cabinet-maker, mason, artisan, craftsperson, craftsman"
                            },
                            {
                                "industry_id": "67",
                                "parent": "62",
                                "child": "Concreting, Paving",
                                "tree": "Construction & Trades >> Concreting, Paving",
                                "thesaurus": "concretor, paver"
                            },
                            {
                                "industry_id": "68",
                                "parent": "62",
                                "child": "Electrical, Lighting",
                                "tree": "Construction & Trades >> Electrical, Lighting",
                                "thesaurus": "sparky, electrician"
                            },
                            {
                                "industry_id": "69",
                                "parent": "62",
                                "child": "Fire & Security Alarm Services",
                                "tree": "Construction & Trades >> Fire & Security Alarm Services",
                                "thesaurus": "electrician"
                            },
                            {
                                "industry_id": "70",
                                "parent": "62",
                                "child": "Gardening",
                                "tree": "Construction & Trades >> Gardening",
                                "thesaurus": "gardener"
                            },
                            {
                                "industry_id": "71",
                                "parent": "62",
                                "child": "Glazing",
                                "tree": "Construction & Trades >> Glazing",
                                "thesaurus": "glazer, glazier"
                            },
                            {
                                "industry_id": "72",
                                "parent": "62",
                                "child": "Household Equipment Repair",
                                "tree": "Construction & Trades >> Household Equipment Repair",
                                "thesaurus": "tradie"
                            },
                            {
                                "industry_id": "73",
                                "parent": "62",
                                "child": "Landscaping",
                                "tree": "Construction & Trades >> Landscaping",
                                "thesaurus": "landscaper, gardener"
                            },
                            {
                                "industry_id": "74",
                                "parent": "62",
                                "child": "Mechanic, Technician",
                                "tree": "Construction & Trades >> Mechanic, Technician",
                                "thesaurus": "auto-elec, car, vehicle, auto, technician"
                            },
                            {
                                "industry_id": "75",
                                "parent": "62",
                                "child": "Motor Vehicle Related Services",
                                "tree": "Construction & Trades >> Motor Vehicle Related Services",
                                "thesaurus": "panel beater, body repairer, automotive repairer, auto repairer, painter, paint, spray, sprayer, car, vehicle, auto, detailer"
                            },
                            {
                                "industry_id": "76",
                                "parent": "62",
                                "child": "Painting & Decorating",
                                "tree": "Construction & Trades >> Painting & Decorating",
                                "thesaurus": "painter, decorator, paint"
                            },
                            {
                                "industry_id": "77",
                                "parent": "62",
                                "child": "Plastering",
                                "tree": "Construction & Trades >> Plastering",
                                "thesaurus": "plasterer"
                            },
                            {
                                "industry_id": "78",
                                "parent": "62",
                                "child": "Plumbing",
                                "tree": "Construction & Trades >> Plumbing",
                                "thesaurus": "plumber"
                            },
                            {
                                "industry_id": "79",
                                "parent": "62",
                                "child": "Property Maintenance, Handyman",
                                "tree": "Construction & Trades >> Property Maintenance, Handyman",
                                "thesaurus": "tradie, caretaker"
                            },
                            {
                                "industry_id": "80",
                                "parent": "62",
                                "child": "Roofing",
                                "tree": "Construction & Trades >> Roofing",
                                "thesaurus": "roofer, roof, tiling"
                            },
                            {
                                "industry_id": "81",
                                "parent": "62",
                                "child": "Steel Fabrication, Welding",
                                "tree": "Construction & Trades >> Steel Fabrication, Welding",
                                "thesaurus": "welder, metal, blacksmith, forger, ironmonger, ironsmith, machinist, frabricator, monger, turner"
                            },
                            {
                                "industry_id": "82",
                                "parent": "62",
                                "child": "Tiling, Carpentry, Floors",
                                "tree": "Construction & Trades >> Tiling, Carpentry, Floors",
                                "thesaurus": "tiler, flooring, floor tiler, wall tiler"
                            },
                            {
                                "industry_id": "83",
                                "parent": "62",
                                "child": "Other",
                                "tree": "Construction & Trades >> Other",
                                "thesaurus": null
                            }
                        ]
                    },
                    {
                        "parent": {
                            "industry_id": "84",
                            "parent": null,
                            "child": "Financial Services & Insurance",
                            "tree": "Financial Services & Insurance >> ",
                            "thesaurus": null
                        },
                        "children": [
                            {
                                "industry_id": "85",
                                "parent": "84",
                                "child": "Accounting, Tax, Bookkeeping Services",
                                "tree": "Financial Services & Insurance >> Accounting, Tax, Bookkeeping Services",
                                "thesaurus": "auditor, accounting, financial, analyst, financial, accounts officer, credit control, accountant, bookkeeper, payroll, taxation, chartered"
                            },
                            {
                                "industry_id": "86",
                                "parent": "84",
                                "child": "Asset Finance",
                                "tree": "Financial Services & Insurance >> Asset Finance",
                                "thesaurus": "broker, finance, asset"
                            },
                            {
                                "industry_id": "87",
                                "parent": "84",
                                "child": "Credit Union Operation",
                                "tree": "Financial Services & Insurance >> Credit Union Operation",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "88",
                                "parent": "84",
                                "child": "Health Insurance",
                                "tree": "Financial Services & Insurance >> Health Insurance",
                                "thesaurus": "broker, insurance, risk"
                            },
                            {
                                "industry_id": "89",
                                "parent": "84",
                                "child": "Life Insurance, Superannuation",
                                "tree": "Financial Services & Insurance >> Life Insurance, Superannuation",
                                "thesaurus": "broker, insurance, risk"
                            },
                            {
                                "industry_id": "90",
                                "parent": "84",
                                "child": "Other",
                                "tree": "Financial Services & Insurance >> Other",
                                "thesaurus": "banker, financial planner"
                            }
                        ]
                    },
                    {
                        "parent": {
                            "industry_id": "91",
                            "parent": null,
                            "child": "Hair & Beauty",
                            "tree": "Hair & Beauty >> ",
                            "thesaurus": null
                        },
                        "children": [
                            {
                                "industry_id": "92",
                                "parent": "91",
                                "child": "Cosmetics Supplies",
                                "tree": "Hair & Beauty >> Cosmetics Supplies",
                                "thesaurus": "cosmetologist, makeup, beauty, skin care, hair, cosmetics"
                            },
                            {
                                "industry_id": "93",
                                "parent": "91",
                                "child": "Day Spas, Health Retreats",
                                "tree": "Hair & Beauty >> Day Spas, Health Retreats",
                                "thesaurus": "massage therapist, spa therapist, reflexology, facial, massage, masseuse, masseur, spa, retreat"
                            },
                            {
                                "industry_id": "94",
                                "parent": "91",
                                "child": "Hair, Beauty Salons",
                                "tree": "Hair & Beauty >> Hair, Beauty Salons",
                                "thesaurus": "barber, barbers, hairdresser, hairdressers, stylist, makup artist, beautician, hair cutter, styler, shaver"
                            },
                            {
                                "industry_id": "95",
                                "parent": "91",
                                "child": "Other",
                                "tree": "Hair & Beauty >> Other",
                                "thesaurus": null
                            }
                        ]
                    },
                    {
                        "parent": {
                            "industry_id": "96",
                            "parent": null,
                            "child": "Health",
                            "tree": "Health >> ",
                            "thesaurus": null
                        },
                        "children": [
                            {
                                "industry_id": "97",
                                "parent": "96",
                                "child": "Chiropractic, Osteopathic Services",
                                "tree": "Health >> Chiropractic, Osteopathic Services",
                                "thesaurus": "chiropractor, osteopath,"
                            },
                            {
                                "industry_id": "98",
                                "parent": "96",
                                "child": "Dental Services",
                                "tree": "Health >> Dental Services",
                                "thesaurus": "dentist, dental hygienist, pediatric dentist,"
                            },
                            {
                                "industry_id": "99",
                                "parent": "96",
                                "child": "General Practice Medical Services",
                                "tree": "Health >> General Practice Medical Services",
                                "thesaurus": "doctor, dr, doc, doctors, physician, clinician, medical practitioner, general practitioner, gp, family practitioner, medical student, student doctor"
                            },
                            {
                                "industry_id": "100",
                                "parent": "96",
                                "child": "Health Foods, Nutrition, Supplements",
                                "tree": "Health >> Health Foods, Nutrition, Supplements",
                                "thesaurus": "organic"
                            },
                            {
                                "industry_id": "101",
                                "parent": "96",
                                "child": "Optometry Services",
                                "tree": "Health >> Optometry Services",
                                "thesaurus": "eye doctor, oculist, optometric physician, optician, optometrist"
                            },
                            {
                                "industry_id": "102",
                                "parent": "96",
                                "child": "Pathology & Imaging Services",
                                "tree": "Health >> Pathology & Imaging Services",
                                "thesaurus": "medical examiner, etiologist, pathologist, radiologist, sonographer, ct radiographer, mri radiographer, mecial imaging technologist"
                            },
                            {
                                "industry_id": "103",
                                "parent": "96",
                                "child": "Physiotherapy Services",
                                "tree": "Health >> Physiotherapy Services",
                                "thesaurus": "physio, physio therapist"
                            },
                            {
                                "industry_id": "104",
                                "parent": "96",
                                "child": "Specialist Medical Services",
                                "tree": "Health >> Specialist Medical Services",
                                "thesaurus": "dermatologist, cosmetic Surgeon, psychologist, psychiatrist, counsellor, anathesiologist, pharmacist, neurologist"
                            },
                            {
                                "industry_id": "105",
                                "parent": "96",
                                "child": "Other",
                                "tree": "Health >> Other",
                                "thesaurus": null
                            }
                        ]
                    },
                    {
                        "parent": {
                            "industry_id": "106",
                            "parent": null,
                            "child": "Hospitality",
                            "tree": "Hospitality >> ",
                            "thesaurus": null
                        },
                        "children": [
                            {
                                "industry_id": "107",
                                "parent": "106",
                                "child": "Accommodation",
                                "tree": "Hospitality >> Accommodation",
                                "thesaurus": "hospitality, hotel, motel, b&b, airbnb, holiday, travel"
                            },
                            {
                                "industry_id": "108",
                                "parent": "106",
                                "child": "Cafes",
                                "tree": "Hospitality >> Cafes",
                                "thesaurus": "cafe, coffee, food, fast food,"
                            },
                            {
                                "industry_id": "109",
                                "parent": "106",
                                "child": "Catering Services",
                                "tree": "Hospitality >> Catering Services",
                                "thesaurus": "hospitality, weddings, events"
                            },
                            {
                                "industry_id": "110",
                                "parent": "106",
                                "child": "Clubs",
                                "tree": "Hospitality >> Clubs",
                                "thesaurus": "club, dance"
                            },
                            {
                                "industry_id": "111",
                                "parent": "106",
                                "child": "Pubs, Bars, Taverns",
                                "tree": "Hospitality >> Pubs, Bars, Taverns",
                                "thesaurus": "bar, pub, hotel, tavern, club, bistro, food"
                            },
                            {
                                "industry_id": "112",
                                "parent": "106",
                                "child": "Restaurants",
                                "tree": "Hospitality >> Restaurants",
                                "thesaurus": "waitress, barista, Front of house, FOH, Kitchen hand, Chef, Cook, Bartender, Bar worker, Waiter, Host, Door person, Dish hand"
                            },
                            {
                                "industry_id": "113",
                                "parent": "106",
                                "child": "Takeaway Food",
                                "tree": "Hospitality >> Takeaway Food",
                                "thesaurus": "fast food, food"
                            },
                            {
                                "industry_id": "114",
                                "parent": "106",
                                "child": "Other",
                                "tree": "Hospitality >> Other",
                                "thesaurus": null
                            }
                        ]
                    },
                    {
                        "parent": {
                            "industry_id": "115",
                            "parent": null,
                            "child": "Manufacturing",
                            "tree": "Manufacturing >> ",
                            "thesaurus": null
                        },
                        "children": [
                            {
                                "industry_id": "116",
                                "parent": "115",
                                "child": "Beverage Manufacturing",
                                "tree": "Manufacturing >> Beverage Manufacturing",
                                "thesaurus": "drink, drinks, beverages"
                            },
                            {
                                "industry_id": "117",
                                "parent": "115",
                                "child": "Clothing, Footwear, Textile Manufacturing",
                                "tree": "Manufacturing >> Clothing, Footwear, Textile Manufacturing",
                                "thesaurus": "garments"
                            },
                            {
                                "industry_id": "118",
                                "parent": "115",
                                "child": "Food Manufacturing",
                                "tree": "Manufacturing >> Food Manufacturing",
                                "thesaurus": "cuisine, grocery"
                            },
                            {
                                "industry_id": "119",
                                "parent": "115",
                                "child": "Furniture Manufacturing",
                                "tree": "Manufacturing >> Furniture Manufacturing",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "120",
                                "parent": "115",
                                "child": "Glass, Ceramic, Cement Manufacturing",
                                "tree": "Manufacturing >> Glass, Ceramic, Cement Manufacturing",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "121",
                                "parent": "115",
                                "child": "Machinery & Equipment Manufacturing",
                                "tree": "Manufacturing >> Machinery & Equipment Manufacturing",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "122",
                                "parent": "115",
                                "child": "Metal Product Manufacturing",
                                "tree": "Manufacturing >> Metal Product Manufacturing",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "123",
                                "parent": "115",
                                "child": "Paper Product Manufacturing",
                                "tree": "Manufacturing >> Paper Product Manufacturing",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "124",
                                "parent": "115",
                                "child": "Printing, Publishing, Media Manufacturing",
                                "tree": "Manufacturing >> Printing, Publishing, Media Manufacturing",
                                "thesaurus": "print"
                            },
                            {
                                "industry_id": "125",
                                "parent": "115",
                                "child": "Wood Product Manufacturing",
                                "tree": "Manufacturing >> Wood Product Manufacturing",
                                "thesaurus": "timber"
                            },
                            {
                                "industry_id": "126",
                                "parent": "115",
                                "child": "Other",
                                "tree": "Manufacturing >> Other",
                                "thesaurus": null
                            }
                        ]
                    },
                    {
                        "parent": {
                            "industry_id": "127",
                            "parent": null,
                            "child": "Primary Industry",
                            "tree": "Primary Industry >> ",
                            "thesaurus": null
                        },
                        "children": [
                            {
                                "industry_id": "128",
                                "parent": "127",
                                "child": "Agriculture",
                                "tree": "Primary Industry >> Agriculture",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "129",
                                "parent": "127",
                                "child": "Commercial Fishing",
                                "tree": "Primary Industry >> Commercial Fishing",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "130",
                                "parent": "127",
                                "child": "Forestry & Logging",
                                "tree": "Primary Industry >> Forestry & Logging",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "131",
                                "parent": "127",
                                "child": "Mining",
                                "tree": "Primary Industry >> Mining",
                                "thesaurus": null
                            }
                        ]
                    },
                    {
                        "parent": {
                            "industry_id": "132",
                            "parent": null,
                            "child": "Professional Services",
                            "tree": "Professional Services >> ",
                            "thesaurus": null
                        },
                        "children": [
                            {
                                "industry_id": "133",
                                "parent": "132",
                                "child": "Architectural Services",
                                "tree": "Professional Services >> Architectural Services",
                                "thesaurus": "architect, designer, home, house"
                            },
                            {
                                "industry_id": "134",
                                "parent": "132",
                                "child": "Child Care Services",
                                "tree": "Professional Services >> Child Care Services",
                                "thesaurus": "day care, kinder, daycare, kindergarten"
                            },
                            {
                                "industry_id": "135",
                                "parent": "132",
                                "child": "Cleaning Services",
                                "tree": "Professional Services >> Cleaning Services",
                                "thesaurus": "housekeeper, cleaner"
                            },
                            {
                                "industry_id": "136",
                                "parent": "132",
                                "child": "Education Services",
                                "tree": "Professional Services >> Education Services",
                                "thesaurus": "teaching, tutor, turtoring, teacher, school, educator"
                            },
                            {
                                "industry_id": "137",
                                "parent": "132",
                                "child": "Engineering Services",
                                "tree": "Professional Services >> Engineering Services",
                                "thesaurus": "engineer, civil, aerospace, automotive biomedical, chemical, electrical, environmental, geological, marine, mechanical"
                            },
                            {
                                "industry_id": "138",
                                "parent": "132",
                                "child": "IT Services",
                                "tree": "Professional Services >> IT Services",
                                "thesaurus": "network, telecommunications, technician, specialist, systems, database, data, administrator, information, development, programming"
                            },
                            {
                                "industry_id": "139",
                                "parent": "132",
                                "child": "Legal Services",
                                "tree": "Professional Services >> Legal Services",
                                "thesaurus": "paralegal, lawyer, litigation, counsel, solicitor, barrister, chartered"
                            },
                            {
                                "industry_id": "140",
                                "parent": "132",
                                "child": "Marketing Services",
                                "tree": "Professional Services >> Marketing Services",
                                "thesaurus": "promotions, brand, content, digita, seo, campaign, ecommerce, email, relations, public, publicity, insights, market, product, social, media, strategist "
                            },
                            {
                                "industry_id": "141",
                                "parent": "132",
                                "child": "Pest Control Services",
                                "tree": "Professional Services >> Pest Control Services",
                                "thesaurus": "exterminator, pest, fumigator, termite"
                            },
                            {
                                "industry_id": "142",
                                "parent": "132",
                                "child": "Property Developers",
                                "tree": "Professional Services >> Property Developers",
                                "thesaurus": "development, estate, home, home, commercial, developer"
                            },
                            {
                                "industry_id": "143",
                                "parent": "132",
                                "child": "Real Estate Services",
                                "tree": "Professional Services >> Real Estate Services",
                                "thesaurus": "agent, property, rent, rental, lease"
                            },
                            {
                                "industry_id": "144",
                                "parent": "132",
                                "child": "Recruitment Services",
                                "tree": "Professional Services >> Recruitment Services",
                                "thesaurus": "recruiter, human resources, hr"
                            },
                            {
                                "industry_id": "145",
                                "parent": "132",
                                "child": "Rental, Hiring Services",
                                "tree": "Professional Services >> Rental, Hiring Services",
                                "thesaurus": "rent, hire"
                            },
                            {
                                "industry_id": "146",
                                "parent": "132",
                                "child": "Storage Services",
                                "tree": "Professional Services >> Storage Services",
                                "thesaurus": "store"
                            },
                            {
                                "industry_id": "147",
                                "parent": "132",
                                "child": "Travel Agent, Tour Services",
                                "tree": "Professional Services >> Travel Agent, Tour Services",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "148",
                                "parent": "132",
                                "child": "Veterinary Services",
                                "tree": "Professional Services >> Veterinary Services",
                                "thesaurus": "vet, dog, groomer, wash"
                            },
                            {
                                "industry_id": "149",
                                "parent": "132",
                                "child": "Other",
                                "tree": "Professional Services >> Other",
                                "thesaurus": null
                            }
                        ]
                    },
                    {
                        "parent": {
                            "industry_id": "150",
                            "parent": null,
                            "child": "Retail",
                            "tree": "Retail >> ",
                            "thesaurus": null
                        },
                        "children": [
                            {
                                "industry_id": "151",
                                "parent": "150",
                                "child": "Antique & Used Goods",
                                "tree": "Retail >> Antique & Used Goods",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "152",
                                "parent": "150",
                                "child": "Clothing, Footwear",
                                "tree": "Retail >> Clothing, Footwear",
                                "thesaurus": "shoes, apparel, clothes, rag trade"
                            },
                            {
                                "industry_id": "153",
                                "parent": "150",
                                "child": "Department Stores",
                                "tree": "Retail >> Department Stores",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "154",
                                "parent": "150",
                                "child": "Flower Retailing",
                                "tree": "Retail >> Flower Retailing",
                                "thesaurus": "floral, florist"
                            },
                            {
                                "industry_id": "155",
                                "parent": "150",
                                "child": "Furniture Retailing",
                                "tree": "Retail >> Furniture Retailing",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "156",
                                "parent": "150",
                                "child": "Garden Supplies",
                                "tree": "Retail >> Garden Supplies",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "157",
                                "parent": "150",
                                "child": "Hardware & Building Supplies",
                                "tree": "Retail >> Hardware & Building Supplies",
                                "thesaurus": "trade, builders"
                            },
                            {
                                "industry_id": "158",
                                "parent": "150",
                                "child": "Homeware Retailing",
                                "tree": "Retail >> Homeware Retailing",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "159",
                                "parent": "150",
                                "child": "Liquor Retailing",
                                "tree": "Retail >> Liquor Retailing",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "160",
                                "parent": "150",
                                "child": "Marine Retailing",
                                "tree": "Retail >> Marine Retailing",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "161",
                                "parent": "150",
                                "child": "Motor Vehicle Retailing",
                                "tree": "Retail >> Motor Vehicle Retailing",
                                "thesaurus": "auto, car, dealer"
                            },
                            {
                                "industry_id": "162",
                                "parent": "150",
                                "child": "Newsagency, Book Retailing",
                                "tree": "Retail >> Newsagency, Book Retailing",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "163",
                                "parent": "150",
                                "child": "Personal Services",
                                "tree": "Retail >> Personal Services",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "164",
                                "parent": "150",
                                "child": "Pharmaceutical Goods",
                                "tree": "Retail >> Pharmaceutical Goods",
                                "thesaurus": "chemist"
                            },
                            {
                                "industry_id": "165",
                                "parent": "150",
                                "child": "Sport & Camping Equipment",
                                "tree": "Retail >> Sport & Camping Equipment",
                                "thesaurus": "camp, outdoor, sporting"
                            },
                            {
                                "industry_id": "166",
                                "parent": "150",
                                "child": "Stationery Goods",
                                "tree": "Retail >> Stationery Goods",
                                "thesaurus": "office"
                            },
                            {
                                "industry_id": "167",
                                "parent": "150",
                                "child": "Supermarket, Grocery & Food Retailing",
                                "tree": "Retail >> Supermarket, Grocery & Food Retailing",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "168",
                                "parent": "150",
                                "child": "Tools & Equipment Retailing",
                                "tree": "Retail >> Tools & Equipment Retailing",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "169",
                                "parent": "150",
                                "child": "Toy & Game Retailing",
                                "tree": "Retail >> Toy & Game Retailing",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "170",
                                "parent": "150",
                                "child": "Watch & Jewellery Retailing",
                                "tree": "Retail >> Watch & Jewellery Retailing",
                                "thesaurus": "jewelry, jeweller"
                            },
                            {
                                "industry_id": "171",
                                "parent": "150",
                                "child": "Other",
                                "tree": "Retail >> Other",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "190",
                                "parent": "150",
                                "child": "Electronics & Electrical Retailing",
                                "tree": "Retail >> Electronics & Electrical Retailing",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "191",
                                "parent": "150",
                                "child": "Online Retailing",
                                "tree": "Retail >> Online Retailing",
                                "thesaurus": "ebay, amazon, ecommerce"
                            }
                        ]
                    },
                    {
                        "parent": {
                            "industry_id": "172",
                            "parent": null,
                            "child": "Transport",
                            "tree": "Transport >> ",
                            "thesaurus": null
                        },
                        "children": [
                            {
                                "industry_id": "173",
                                "parent": "172",
                                "child": "Freight, Courier, Pick-up Services",
                                "tree": "Transport >> Freight, Courier, Pick-up Services",
                                "thesaurus": "driver, shipping, van, post"
                            },
                            {
                                "industry_id": "174",
                                "parent": "172",
                                "child": "Taxi, Uber Services",
                                "tree": "Transport >> Taxi, Uber Services",
                                "thesaurus": "driver, cab"
                            },
                            {
                                "industry_id": "175",
                                "parent": "172",
                                "child": "Rail Transport",
                                "tree": "Transport >> Rail Transport",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "176",
                                "parent": "172",
                                "child": "Road Transport",
                                "tree": "Transport >> Road Transport",
                                "thesaurus": "driver, truck, van"
                            },
                            {
                                "industry_id": "177",
                                "parent": "172",
                                "child": "Water Transport",
                                "tree": "Transport >> Water Transport",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "178",
                                "parent": "172",
                                "child": "Other",
                                "tree": "Transport >> Other",
                                "thesaurus": null
                            }
                        ]
                    },
                    {
                        "parent": {
                            "industry_id": "179",
                            "parent": null,
                            "child": "Wholesale Trade",
                            "tree": "Wholesale Trade >> ",
                            "thesaurus": null
                        },
                        "children": [
                            {
                                "industry_id": "180",
                                "parent": "179",
                                "child": "Builders Supplies Wholesaling",
                                "tree": "Wholesale Trade >> Builders Supplies Wholesaling",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "181",
                                "parent": "179",
                                "child": "Farm Produce Wholesaling",
                                "tree": "Wholesale Trade >> Farm Produce Wholesaling",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "182",
                                "parent": "179",
                                "child": "Food & Drink Wholesaling",
                                "tree": "Wholesale Trade >> Food & Drink Wholesaling",
                                "thesaurus": "drink, drinks, beverages, cusine, grocery"
                            },
                            {
                                "industry_id": "183",
                                "parent": "179",
                                "child": "Household Good Wholesaling",
                                "tree": "Wholesale Trade >> Household Good Wholesaling",
                                "thesaurus": "furniture, white goods"
                            },
                            {
                                "industry_id": "184",
                                "parent": "179",
                                "child": "Machinery & Equipment Wholesaling",
                                "tree": "Wholesale Trade >> Machinery & Equipment Wholesaling",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "185",
                                "parent": "179",
                                "child": "Mineral, Metal & Chemical Wholesaling",
                                "tree": "Wholesale Trade >> Mineral, Metal & Chemical Wholesaling",
                                "thesaurus": null
                            },
                            {
                                "industry_id": "186",
                                "parent": "179",
                                "child": "Motor Vehicle Wholesaling",
                                "tree": "Wholesale Trade >> Motor Vehicle Wholesaling",
                                "thesaurus": "auto, car, dealer"
                            },
                            {
                                "industry_id": "187",
                                "parent": "179",
                                "child": "Clothing, Footwear, Textile Wholesaling",
                                "tree": "Wholesale Trade >> Clothing, Footwear, Textile Wholesaling",
                                "thesaurus": "shoes, apparel, clothes, rag"
                            },
                            {
                                "industry_id": "188",
                                "parent": "179",
                                "child": "Other",
                                "tree": "Wholesale Trade >> Other",
                                "thesaurus": null
                            }
                        ]
                    },
                    {
                        "parent": {
                            "industry_id": "189",
                            "parent": null,
                            "child": "Other",
                            "tree": "Other >> ",
                            "thesaurus": null
                        }
                    }
                ],
                "home_owner": [
                    "yes",
                    "no"
                ]
            };
            this.selectedFilterItems = {
                "partner_user_id": [
                    418,
                    801,
                    802,
                    803,
                    805,
                    813,
                    814,
                    843,
                    859,
                    890,
                    916,
                    923,
                    925,
                    961
                ],
                "start_date": "2021-01-01 00:00:00",
                "end_date": "2021-10-18 23:59:59",
                "source": [
                    "Partners",
                    "App",
                    "PartnerAPI"
                ],
                "campaign": [
                    "projv19"
                ],
                "lender_id": [
                    1,
                    3,
                    5,
                    6,
                    7,
                    8,
                    9,
                    10,
                    14,
                    15,
                    17,
                    18,
                    19,
                    20,
                    23,
                    24,
                    25,
                    26,
                    27,
                    33,
                    35,
                    36,
                    41,
                    47,
                    48,
                    54,
                    56,
                    59,
                    61,
                    63,
                    64,
                    67,
                    69,
                    70,
                    71,
                    72,
                    73,
                    74,
                    76,
                    77,
                    78,
                    81,
                    82,
                    83,
                    84,
                    85,
                    86,
                    87,
                    88,
                    89,
                    90,
                    92,
                    93,
                    94
                ],
                "status": [
                    "Attempting",
                    "In Progress",
                    "Pending",
                    "Rejected",
                    "Settled"
                ],
                "loan_amount": {
                    "min": 0,
                    "max": 100000
                },
                "product_type_id": [
                    1,
                    2,
                    3,
                    4,
                    5,
                    6,
                    7,
                    8,
                    9,
                    10,
                    11,
                    14,
                    15,
                    16,
                    17,
                    18,
                    19,
                    20,
                    21,
                    22,
                    23,
                    24
                ],
                "purpose_id": [
                    1,
                    2,
                    3,
                    4,
                    5,
                    6,
                    7,
                    8,
                    9,
                    10,
                    11,
                    12
                ],
                "state": [
                    "ACT",
                    "NSW",
                    "VIC",
                    "QLD",
                    "SA",
                    "WA",
                    "TAS",
                    "NT"
                ],
                "industry_id": [
                    52,
                    53,
                    54,
                    55,
                    56,
                    57,
                    58,
                    59,
                    60,
                    61,
                    62,
                    63,
                    64,
                    65,
                    66,
                    67,
                    68,
                    69,
                    70,
                    71,
                    72,
                    73,
                    74,
                    75,
                    76,
                    77,
                    78,
                    79,
                    80,
                    81,
                    82,
                    83,
                    84,
                    85,
                    86,
                    87,
                    88,
                    89,
                    90,
                    91,
                    92,
                    93,
                    94,
                    95,
                    96,
                    97,
                    98,
                    99,
                    100,
                    101,
                    102,
                    103,
                    104,
                    105,
                    106,
                    107,
                    108,
                    109,
                    110,
                    111,
                    112,
                    113,
                    114,
                    115,
                    116,
                    117,
                    118,
                    119,
                    120,
                    121,
                    122,
                    123,
                    124,
                    125,
                    126,
                    127,
                    128,
                    129,
                    130,
                    131,
                    132,
                    133,
                    134,
                    135,
                    136,
                    137,
                    138,
                    139,
                    140,
                    141,
                    142,
                    143,
                    144,
                    145,
                    146,
                    147,
                    148,
                    149,
                    150,
                    151,
                    152,
                    153,
                    154,
                    155,
                    156,
                    157,
                    158,
                    159,
                    160,
                    161,
                    162,
                    163,
                    164,
                    165,
                    166,
                    167,
                    168,
                    169,
                    170,
                    171,
                    172,
                    173,
                    174,
                    175,
                    176,
                    177,
                    178,
                    179,
                    180,
                    181,
                    182,
                    183,
                    184,
                    185,
                    186,
                    187,
                    188,
                    189,
                    190,
                    191
                ],
                "home_owner": [
                    "yes",
                    "no"
                ],
                "asset": {
                    "contract_type": [
                        "low doc",
                        "full doc"
                    ],
                    "equipment_id": [
                        1,
                        2,
                        3,
                        4,
                        5,
                        6,
                        7,
                        11,
                        13,
                        14,
                        15,
                        16,
                        17,
                        18,
                        19,
                        20,
                        21,
                        22,
                        23,
                        24,
                        25,
                        26,
                        27,
                        28,
                        29,
                        30,
                        31,
                        32,
                        33,
                        34,
                        35,
                        36,
                        37,
                        38,
                        39,
                        40,
                        41,
                        42,
                        43,
                        44,
                        45,
                        46,
                        47,
                        48,
                        49,
                        50,
                        51,
                        52,
                        53,
                        54,
                        55,
                        56,
                        57,
                        58,
                        59,
                        60,
                        61,
                        62,
                        63,
                        64,
                        65,
                        66,
                        67,
                        68,
                        69,
                        70,
                        71,
                        72,
                        73,
                        74,
                        75,
                        76,
                        77,
                        78,
                        79,
                        80,
                        81,
                        82,
                        83,
                        84,
                        85,
                        86,
                        87,
                        88,
                        89,
                        90,
                        91,
                        92,
                        93,
                        94,
                        95,
                        96,
                        97,
                        98,
                        99,
                        100,
                        101,
                        102,
                        103,
                        104,
                        105,
                        106,
                        107,
                        108,
                        109,
                        110,
                        111,
                        112,
                        113,
                        114,
                        115,
                        116,
                        117,
                        118,
                        119,
                        120,
                        121,
                        122,
                        123
                    ],
                    "age": {
                        "min": 0,
                        "max": 10
                    }
                }
            }
            this.fetchChartDataMock()
        },

        fetchChartDataMock() {
            this.chartData = {
                "single_figures": {
                    "loan_book": {
                        "total": 54899,
                        "average": 27449.5
                    },
                    "commission": {
                        "total": 2744.95,
                        "average": 1372.475
                    },
                    "deals": {
                        "in_pipeline": 18,
                        "won": 2,
                        "lost": 6
                    }
                },
                "loan_amount_by_status": [
                    {
                        "group_name": "In Progress",
                        "total_loan_amount_requested": 25000
                    },
                    {
                        "group_name": "Pending",
                        "total_loan_amount_requested": 397000
                    },
                    {
                        "group_name": "Rejected",
                        "total_loan_amount_requested": 76500
                    },
                    {
                        "group_name": "Settled",
                        "total_loan_amount_requested": 220000
                    }
                ],
                "loan_amount_by_lender": [
                    {
                        "lender_name": "Prospa",
                        "total_funded_amount": 54899,
                        "average_funded_amount": 27449.5
                    }
                ],
                "count_of_product_type": [
                    {
                        "product_type_name": "Unsecured Loan",
                        "total": 16
                    }
                ],
                "loan_amount_by_user": {
                    "user_890": [
                        {
                            "partner_user_id": 890,
                            "name": "Tiffany Chu",
                            "lead_created": "2021-06-22",
                            "total_amount_requested": 50000
                        }
                    ],
                    "user_923": [
                        {
                            "partner_user_id": 923,
                            "name": "Eric Leao",
                            "lead_created": "2021-06-02",
                            "total_amount_requested": 0
                        },
                        {
                            "partner_user_id": 923,
                            "name": "Eric Leao",
                            "lead_created": "2021-06-03",
                            "total_amount_requested": 22000
                        },
                        {
                            "partner_user_id": 923,
                            "name": "Eric Leao",
                            "lead_created": "2021-06-09",
                            "total_amount_requested": 55000
                        },
                        {
                            "partner_user_id": 923,
                            "name": "Eric Leao",
                            "lead_created": "2021-06-11",
                            "total_amount_requested": 50000
                        },
                        {
                            "partner_user_id": 923,
                            "name": "Eric Leao",
                            "lead_created": "2021-06-15",
                            "total_amount_requested": 13000
                        },
                        {
                            "partner_user_id": 923,
                            "name": "Eric Leao",
                            "lead_created": "2021-06-16",
                            "total_amount_requested": 22000
                        },
                        {
                            "partner_user_id": 923,
                            "name": "Eric Leao",
                            "lead_created": "2021-06-21",
                            "total_amount_requested": 0
                        },
                        {
                            "partner_user_id": 923,
                            "name": "Eric Leao",
                            "lead_created": "2021-06-24",
                            "total_amount_requested": 20000
                        }
                    ]
                },
                "funded_and_total_commission": [
                    {
                        "funded_date": "2021-06",
                        "total_funded_amount": 54899,
                        "total_commission": 2744.95
                    }
                ],
                "lend_score_by_lead_count": [
                    {
                        "score_0_20": 4,
                        "score_21_40": 1,
                        "score_41_60": 1,
                        "score_61_80": 0,
                        "score_81_100": 0
                    }
                ]
            }
        },

        handleFilterChangeMock() {
            alert("refetch data with new filter, chart data should be updated");
            this.fetchChartDataMock()
        },

    }
}
</script>
