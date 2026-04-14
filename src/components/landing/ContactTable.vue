<script>
import { Funnel, Search, ChevronDown, MoveRight } from '@lucide/vue'
export default {
    components: {
        Funnel,
        Search,
        ChevronDown,
        MoveRight
    },
    name: 'ContactTable',
    data() {
        return {
           searchQuery: '',
           contacts:[
  { 
    name: 'Ana Santos', 
    email: 'ana@company.co', 
    status: 'active', 
    initials: 'AS', 
    initialsBg: 'bg-emerald-500' 
  },
  { 
    name: 'Marco Reyes', 
    email: 'marco@startup.io', 
    status: 'pending', 
    initials: 'MR', 
    initialsBg: 'bg-(--emerald-medium)' 
  },
  { 
    name: 'Jane Dela Cruz', 
    email: 'jane@agency.ph', 
    status: 'active', 
    initials: 'JD', 
    initialsBg: 'bg-indigo-500' 
  },
  { 
    name: 'Kim Lee', 
    email: 'kim@design.co', 
    status: 'inactive', 
    initials: 'KL', 
    initialsBg: 'bg-pink-500' 
  }
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
    <div class="contact flex flex-col items-center gap-4 bg-(--emerald-mint)">
 
           <span class="text-xs font-semibold px-4 py-2 rounded-full bg-(--emerald-light) text-(--emerald-dark)">LIVE PREVIEW</span>
        <h3 class="text-3xl font-bold">See it in action</h3>
        <p class="font-thin text-xs text-(--emerald-medium)">Try searching and filtering contacts in real-time.</p>
    
    <div class="bg-white rounded-2xl p-6 shadow-lg border border-(--emerald-light)">
        <div class="flex gap-2 flex-col sm:flex-row w-full">
            <div class="relative grow">
                <input type="text"
                 v-model="searchQuery" 
                 placeholder="Search contacts..."
                 class="bg-(--emerald-surface) px-4 py-2 pl-10 h-12 rounded-2xl border border-(--emerald-light) focus:outline-none focus:ring-2 focus:ring-(--emerald-pale) focus:border-transparent w-full">
                <Search class="absolute left-3 top-1/2 transform -translate-y-1/2 text-(--emerald-medium)" />
            </div> 
            <button class="flex items-center gap-2 bg-(--emerald-surface) rounded-2xl border border-(--emerald-light) px-6 py-2 whitespace-nowrap"><span><Funnel /></span>All Status <span><ChevronDown class="text-(--emerald-medium)" /></span> </button>
        </div>
        <p class="text-xs text-(--emerald-medium) py-4 font-semibold">Showing 4 of 12 contacts</p>
        
        
        <div class="md:hidden">
            <div v-for="contact in filteredContacts" :key="contact.email" class="bg-white p-4 border border-(--emerald-light)">
                <div class="flex items-center">
                    <div :class="`${contact.initialsBg} w-12 h-12 rounded-full flex items-center justify-center text-white font-semibold text-lg`">
                        {{ contact.initials }}
                    </div>
                    
                        <h4 class="font-semibold text-(--emerald-dark)">{{ contact.name }}</h4>
                        <p class="text-xs text-(--emerald-medium)">{{ contact.email }}</p>
                   
                </div>
             
                    <span :class="`px-3 py-1 rounded-full text-xs font-semibold ${
                        contact.status === 'active' ? 'bg-(--emerald-light) text-(--emerald-dark)' :
                        contact.status === 'pending' ? 'bg-(--amber-100) text-(--amber-600)' :
                        'bg-(--red-100) text-(--red-500)'
                    }`">
                        {{ contact.status.charAt(0).toUpperCase() + contact.status.slice(1) }}
                    </span>
                    <button class="flex items-center gap-1 text-(--emerald) font-semibold text-sm">
                        View <MoveRight class="w-4 h-4" />
                    </button>
               
            </div>
        </div>

       
        <table class="hidden md:table w-full rounded-3xl border border-(--emerald-light)">
            <thead class="bg-(--emerald-surface)">
                <tr>
                    <th class="text-left px-4 py-3 text-xs font-semibold text-(--emerald-dark) ">NAME</th>
                    <th class=" py-3 text-xs font-semibold text-(--emerald-dark) ">EMAIL</th>
                    <th class="  py-3 text-xs font-semibold text-(--emerald-dark) ">STATUS</th>
                    <th class="  py-3 text-xs font-semibold text-(--emerald-dark) ">ACTIONS</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="contact in filteredContacts" :key="contact.email" class="border-b border-(--emerald-light)">
                    <td class="px-4 py-3">
                        <div class="flex items-center gap-3">
                            <div :class="`${contact.initialsBg} w-10 h-10 rounded-full flex items-center justify-center text-white font-semibold text-sm`">
                                {{ contact.initials }}
                            </div>
                            <span class="font-medium text-(--emerald-dark)">{{ contact.name }}</span>
                        </div>
                    </td>
                    <td class="px-4 py-3 text-(--emerald-medium)">{{ contact.email }}</td>
                    <td class="px-4 py-3">
                        <span :class="`px-3 py-1 rounded-full text-xs font-semibold ${
                            contact.status === 'active' ? 'bg-(--emerald-light) text-(--emerald-dark)' :
                            contact.status === 'pending' ? 'bg-(--amber-100) text-(--amber-600)' :
                            'bg-(--red-100) text-(--red-500)'
                        }`">
                            {{ contact.status.charAt(0).toUpperCase() + contact.status.slice(1) }}
                        </span>
                    </td>
                    <td class="px-4 py-3 text-right">
                        <button class="flex items-center gap-1 text-(--emerald) font-semibold text-sm">
                            View <MoveRight class="w-4 h-4" />
                        </button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
    </div>
   
</template>