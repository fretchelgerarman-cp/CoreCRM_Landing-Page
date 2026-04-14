<script>
import { Funnel, Search } from '@lucide/vue'
export default {
    components: {
        Funnel,
        Search
    },
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
    <div class="contact flex flex-col items-center gap-4">
 
           <span class="text-xs font-semibold px-4 py-2 rounded-full bg-(--emerald-light) text-(--emerald-dark)">LIVE PREVIEW</span>
        <h3 class="text-3xl font-bold">See it in action</h3>
        <p class="font-thin text-xs text-(--emerald-medium)">Try searching and filtering contacts in real-time.</p>
    
    <div>
        <div class="flex gap-2 flex-col sm:flex-row w-full max-w-md">
            <div class="relative">
                <input type="text"
                 v-model="searchQuery" 
                 placeholder="Search contacts..."
                 class="bg-(--emerald-surface) px-4 py-2 pl-10 h-12 rounded-2xl border border-(--emerald-light) focus:outline-none focus:ring-2 focus:ring-(--emerald-pale) focus:border-transparent">
                <Search class="absolute left-3 top-1/2 transform -translate-y-1/2 text-(--emerald-medium)" />
            </div>
            <button class="flex items-center gap-2 bg-(--emerald-surface) rounded-2xl border border-(--emerald-light) px-6 py-2"><span><Funnel /></span>All Status</button>
        </div>
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
    </div>
   
</template>