<template>
    <div>
        <template v-if="authenticated">
            <h2>{{ user.username }} Dashboard</h2>
            <p>This is the Dashboard page</p>
            <table>
                <caption>User actions</caption>
                <tr>
                    <th id="lastlogin">Last Login Date</th>
                    <th id="tokenexpiry">Token Expiry Date</th>
                    <th id="userstatus">Status</th>
                </tr>
                <tr>
                    <td>{{ new Date(user.lastLogin).getDate()+'-'+(new Date(user.lastLogin).getMonth()+1)+'-'+(new Date(user.lastLogin).getFullYear()) }}</td>
                    <td>{{ new Date(user.tokenExpiry).getDate()+'-'+(new Date(user.tokenExpiry).getMonth()+1)+'-'+(new Date(user.tokenExpiry).getFullYear()) }}</td>
                    <td>{{ user.status }} </td>
                </tr>
            </table>
        </template>
    </div>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
    name: 'dashboard',
    components: {
        
    },

    computed: {
        ...mapGetters ({
            authenticated: 'auth/authenticated',
            user: 'auth/user',
        })
    },
}
</script>
