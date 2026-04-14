<script>
export default {
    name: 'ContactTable',
    data() {
        return {
           searchQuery: '',
           contacts: [
            { name: 'John Doe', email: 'john.doe@example.com' , status: 'active'},
            { name: 'Jane Smith', email: 'jane.smith@example.com' , status: 'inactive'}
           ]
        }
    },
    computed: {
        filteredContacts() {
            return this.contacts.filter(contact => 
                contact.name.toLowerCase().includes(this.searchQuery.toLowerCase()) ||
                contact.email.toLowerCase().includes(this.searchQuery.toLowerCase())
            )
        }
    }
}
</script>

<template>
    <div>
        <input type="text" v-model="searchQuery" placeholder="Search contacts...">
        <button>Search</button>
        <table>
            <thead>
                <tr>
                    <th>Name</th>
                    <th>Email</th>
                    <th>Status</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="contact in filteredContacts" :key="contact.email">
                    <td>{{ contact.name }}</td>
                    <td>{{ contact.email }}</td>
                    <td>{{ contact.status }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>