<template>
    <div>

        <Message :msg="msg" v-show="msg"/>

        <div >
            <form action="#" id="burger-form" @submit="createBurguer($event)">
                <div class="input-container">
                    <label for="nome">Nome do cliente:</label>
                    <input type="text" name="nome" id="nome" placeholder="Digite o seu nome" v-model="nome">
                </div>

                <div class="input-container">
                    <label for="pao">Escolha o pão:</label>
                    <select name="pao" id="pao" v-model="pao">
                        <option value="">Selecione o tipo de pão</option>
                        <option v-for="pao in paes" :key="pao.id" :value="pao.tipo" >{{ pao.tipo }}</option>
                    </select>
                </div>

                <div class="input-container">
                    <label for="carne">Escolha a carne:</label>
                    <select name="carne" id="carne" v-model="carne">
                        <option value="">Selecione o tipo de carne</option>
                        <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{ carne.tipo }}</option>
                    </select>
                </div>

                <div id="opcionais-container" class="input-container">
                    <label for="opcionais-label" id="opcionais">Selecione os opcionais:</label>
                    <div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id">
                        <input type="checkbox" name="opcionais" id="opcionais" v-model="opcionais" :value="opcional.tipo">
                        <span>{{opcional.tipo}}</span>
                    </div>
                    
                    
                </div>

                <div class="input-container">
                    <input type="submit" value="Criar meu Burger!" class="submit-btn">
                </div>
            </form>
        </div>
    </div>
</template>

<script>
import Message from '../components/Message.vue';

export default {
    name: "BurgerForm",
    components: {
        Message
    },
    data(){
        return {
            paes: "",
            carnes: "",
            opcionaisdata: "",
            nome: "",
            pao: "",
            carne: "",
            opcionais: [],
            msg: null
        }
    },
    methods: {
        async getIngredientes(){
            const req = await fetch("http://localhost:3000/ingredientes");

            const data = await req.json();

            this.paes = data.paes;
            this.carnes = data.carnes;
            this.opcionaisdata = data.opcionais;
            
        },
        async createBurguer(e){
            e.preventDefault();

            const data = {
                nome: this.nome,
                carne: this.carne,
                pao: this.pao,
                opcionais: Array.from(this.opcionais),
                status: "Solicitado"
            }

            const dataJson = JSON.stringify(data);
            const req = await fetch("http://localhost:3000/burgers", {
               method: "POST",
               headers: {"Content-Type": "application/json"},
               body: dataJson 
            });

            const res = await req.json();

            //msg de sistema
            this.msg = `Pedido N ${res.id} realizado com sucesso`

            setTimeout(()=> this.msg = "", 3000);
            //limpar campos
            this.nome = "";
            this.carne = "";
            this.pao = "";
            this.opcionais = "";
            

        }
    },
    mounted() {
        this.getIngredientes();
    }
}
</script>

<style scoped>
    #burger-form {
        max-width: 600px;
        margin: 0 auto;
        
    }

    .input-container {
        max-width: 400px;
        display: flex;
        flex-direction: column;
        margin-bottom: 20px;
    }

    label {
        font-weight: bold;
        margin-bottom: 15px;
        color: #222;
        padding: 5px 10px;
        border-left: 4px solid #FCBA03;

    }

    input,select {
        padding: 5px 10px;
        width: 300px;

    }

    #opcionais-container{
        flex-direction: row;
        flex-wrap: wrap;
    }

    #opcionais-label {
        width: 100%;
    }

    .checkbox-container{
        display: flex;
        align-items: start;
        width: 50%;
        margin-bottom: 20px;
    }

    .checkbox-container span, .checkbox-container input{
        margin-left: 6px;
        font-weight: bold;
    }

    .submit-btn{
        background-color: #222;
        color: #FCBA03;
        font-weight: bold;
        border: 2px solid #222;
        padding: 10px;
        font-size: 16px;
        margin: 0 auto;
        cursor: pointer;
        transition: .3s;
    }

    .submit-btn:hover{
        background-color: transparent;
        color: #222;
    }

</style>