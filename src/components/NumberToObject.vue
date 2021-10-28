<template>
    <div>
        NumberToObject.vue
    </div>
</template>

<script>
export default {
    mounted() {
        let users = [
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
        ];
        let userIds = [418, 801, 961];
        let usersWithNameAndId = this.mapToObject(userIds, users);

        this.mapToNumber(usersWithNameAndId)
    },
    methods: {
        mapToObject(userIds, users) {
            let emptyArray = [];
            for (let i = 0; i < userIds.length; i++) {

                let foundIndex = users.findIndex(user => user.partner_user_id == userIds[i]);
                let foundUser = users[foundIndex];


                let user = {
                    "partner_user_id": userIds[i],
                    "name": foundUser.name
                };

                emptyArray.push(user)
            }

            console.log(emptyArray)
            return emptyArray;

            // ------------------------

            // let mapped = userIds.map((id, index) => {
            //     let foundIndex = users.findIndex(user => user.partner_user_id == userIds[index]);
            //     let foundUser = users[foundIndex];
            //
            //     return {
            //         "partner_user_id": id,
            //         "name": foundUser.name
            //     };
            // })
            //
            // console.log(mapped)
            // return mapped
        },

        mapToNumber(usersWithNameAndId) {
            let mapped = usersWithNameAndId.map(userObject => {
                return userObject.partner_user_id;
            })
            console.log(mapped)

            return mapped;
        },
    }
}
</script>
