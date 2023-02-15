<template>
    <div>
        <table id="generalControlOfTables">
            <tr class="header">
                <td> Code </td>
                <td> Name </td>
                <td> Age </td>
                <td> Zip Code </td>
                <td> City </td>
                <td> State </td>
                <td> Agency </td>
                <td> Active Account </td>
                <td> Delete Item Button </td>
            </tr>
            <tr class="btn" v-for="arrayClient in client" :key="arrayClient.id">
                <td v-if="!edit" @click="editionItemArray"> {{ arrayClient.Code }}</td>
                <input v-else type="text" v-model="arrayClient.Code" v-on:keyup.enter="edit = false">

                <td v-if="!edit" @click="editionItemArray"> {{ arrayClient.Name }}</td>
                <input v-else type="text" v-model="arrayClient.Name" v-on:keyup.enter="edit = false">

                <td v-if="!edit" @click="editionItemArray"> {{ arrayClient.Age }}</td>
                <input v-else type="text" v-model="arrayClient.Age" v-on:keyup.enter="edit = false">

                <td v-if="!edit" @click="editionItemArray"> {{ arrayClient.ZipCode }}</td>
                <input v-else type="text" v-model="arrayClient.ZipCode" v-on:keyup.enter="edit = false">

                <td v-if="!edit" @click="editionItemArray"> {{ arrayClient.Place.City }}</td>
                <input v-else type="text" v-model="arrayClient.Place.City" v-on:keyup.enter="edit = false">

                <td v-if="!edit" @click="editionItemArray"> {{ arrayClient.Place.State }}</td>
                <input v-else type="text" v-model="arrayClient.Place.State" v-on:keyup.enter="edit = false">
                
                <td v-if="!edit" @click="editionItemArray"> {{ arrayClient.Bank.Agency }}</td>
                <input v-else type="text" v-model="arrayClient.Bank.Agency" v-on:keyup.enter="edit = false">

                <td v-if="!edit" @click="editionItemArray"> {{ arrayClient.Bank.Active }}</td>
                <input v-else type="text" v-model="arrayClient.Bank.Active" v-on:keyup.enter="edit = false">

                <button type="button" @click="RemoveItem(arrayClient.Code)"> Remove Item</button>
            </tr>
            <button type="button" @click="AddItem"> Adding Item </button>
        </table>
    </div>
    
</template>

<script>
export default {
    data(){
        return {
            increasingNumber: 2,
            edit: false,
            client: [
                {
                    Code: 1,
                    Name: "Krhistopher",
                    Age: 25,
                    ZipCode: 83405310,
                    Place: {
                        City: "Curitiba",
                        State: "Paraná"
                    },
                    Bank: {
                        Agency: 'Itau',
                        Active: true
                    }
                },
                {
                    Code: 2,
                    Name: "Amaral",
                    Age: 25,
                    ZipCode: 83405310,
                    Place: {
                        City: "Pulicia",
                        State: "Radical"
                    },
                    Bank: {
                        Agency: 'Bradesco',
                        Active: true
                    }
                }
                
            ]
        }
    },
    methods: {
        RemoveItem(catchingClickEvent){
            console.log(catchingClickEvent + "Clique do mouse")

            const elementIndex = this.client.findIndex((checkNumber) => {
                return checkNumber.Code == catchingClickEvent
            })

            this.client.splice(elementIndex, 1)

        },
        AddItem(){
            this.increasingNumber++
            const newItemInObject = {
                    Code: this.increasingNumber,
                    Name: "Amaral O Policial Radical",
                    Age: 25,
                    ZipCode: 83405310,
                    Place: {
                        City: "Ghotam",
                        State: "Lutando"
                    },
                    Bank: {
                        Agency: 'Bradesco',
                        Active: true
                    }
                }

                return this.client.push(newItemInObject)

        },
        editionItemArray(){
            this.edit = true
        },


    }
    
}
</script>

<style scoped>

#generalControlOfTables {
    border: 1px solid black;
    flex-wrap: wrap;
    
}

.btn {
    cursor: pointer;
}

</style>