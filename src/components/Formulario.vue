<script setup>
const props = defineProps(['insereValor', 'resultado']);

</script>

<template>
    <div class="container rounded-3 bg-light form-container">
        <form>
            <div class="row m-0">

                <div class="col-3 ">

                    <div class="row m-0">
                        <input @change="props.insereValor" type="number" class="form-control mb-3" placeholder="Primeiro valor" id="input_valorA">
                    </div>

                    <div class="row m-0">
                        <select @change="props.insereValor" class="mb-3 form-control" id="select_operacao">
                            <option value="adicao">Adição</option>
                            <option value="subtracao">Subtração</option>
                            <option value="multiplicacao">Multiplicação</option>
                            <option value="divisao">Divisão</option>
                        </select>
                    </div>

                    <div class="row m-0">
                        <input @change="props.insereValor" type="number" class="form-control mb-3" placeholder="Segundo valor" id="input_valorB">
                    </div>

                </div>

                <div class="col-9">
                    <div class="cell rounded-3 cell__big">
                        <p>{{props.resultado}}</p>
                    </div>
                </div>

            </div>
        </form>
    </div>

</template>

<style scoped>
.form-container {
    min-height: 50vh;
    padding: 24px;
    display: flex;
    justify-content: center;
    align-items: center;    
}

form {
    width: 80%;
    padding: 16px;
}

.form-control {
        height: 40px;
        border: none;
        border-bottom: 1px solid #333;
        width: 100%;
        background: 0 0;
        font-weight: 600;
    }

.cell {
    min-height: 100px;
}

.cell__big {
    background-color: #FFFFFF;
    height: auto;
    display: flex;
    height: 100%;
    justify-content: center;
    align-items: center;
    border-bottom: solid 3px #120779;
}

p {
    font-size: 6em;
    font-weight: 700;
}
</style>