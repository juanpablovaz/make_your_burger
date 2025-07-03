<template>
    <div>

        <p>Componente de mensagem</p>

        <div >
            <form action="#" id="burger-form">
                <div class="input-container">
                    <label for="nome">Nome do cliente:</label>
                    <input type="text" name="nome" id="nome" placeholder="Digite o seu nome" v-model="nome">
                </div>

                <div class="input-container">
                    <label for="pao">Escolha o pão:</label>
                    <select name="pao" id="pao" v-model="pao">
                        <option value="">Selecione o seu pão</option>
                        <option value=""></option>
                    </select>
                </div>

                <div class="input-container">
                    <label for="carne">Escolha a carne do seu Burger:</label>
                    <select name="carne" id="carne" v-model="carne">
                        <option value="">Selecione o tipo de carne</option>
                        <option value="1">1</option>
                    </select>
                </div>

                <div id="opcionais-container" class="input-container">
                    <label for="opcionais-label" id="opcionais">Selecione os opcionais:</label>
                    <div class="checkbox-container">
                        <input type="checkbox" name="opcionais" id="opcionais" v-model="opcionais" value="salame">
                        <span>Salame</span>
                    </div>
                    <div class="checkbox-container">
                        <input type="checkbox" name="opcionais" id="opcionais" v-model="opcionais" value="salame">
                        <span>Salame</span>
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
export default {
    name: "BurgerForm"
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