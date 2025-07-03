<template>
<div id="burger-table">
    <div>
        <div id="burger-table-heading">
            <div class="order-id">#:</div>
            <div>Cliente:</div>
            <div>Pao:</div>
            <div>Carne:</div>
            <div>Opcionais:</div>
            <div>Ações:</div>
        </div>

        <div id="burger-table-rows">
            <div class="burger-table-row">
                <div class="order-number">1</div>
                <div>Joao</div>
                <div>Pao</div>
                <div>Maminha</div>
                <div>
                    <ul>
                        <li>salame</li>
                    </ul>
                </div>
                <div>
                    <select name="status" id="" class="status">
                        <option value="">Selecione o status do Burger</option>
                    </select>
                    <button class="delete-btn">Cancelar</button>
                </div>

            </div>
        </div>
    </div>

</div>
</template>

<script>
export default {
    name: "Dashboard"
}
</script>

<style scoped>


</style>