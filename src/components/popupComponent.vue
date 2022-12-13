<template>
    <div class="modal-shadow" @click.self="closePopup">
        <div class="popup">
            <h3 class="popup__title">Выберите желаемое количество</h3>
            <div class="popup__footer">
                <label for="btc">
                    <input v-model="btc" type="number" min="0" @change="ConvertBtc" name="btc"
                        class="popup__footer_btc popup__footer_input">
                    Bitcoin
                </label>

                <label for="rub">
                    <input v-model="rub" type="number" min="0" @change="ConvertRub" name="rub"
                        class="popup__footer_rub popup__footer_input">
                    Рубли
                </label>
            </div>
        </div>
    </div>
</template>
  
<script>
export default {
    data() {
        return {
            isInfoPopupVisible: false,
            btc: null,
            rub: null
        };
    },
    methods: {
        closePopup() {
            this.$emit("openPopup");
        },
        ConvertBtc() {
            this.rub = null
            let price = this.btc * 107234480
            this.rub = price
        },
        ConvertRub() {
            this.btc = null
            let jopa = this.rub / 107234480
            this.btc = jopa
        }

    }
};
</script>
  
<style lang="scss" scoped>
* {
    background-color: #ffffff;
    color: #17191F;
}

.modal-shadow {
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
    width: 100%;
    background: rgba(0, 0, 0, 0.3);
}

.popup {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    // width: 45%;
    padding: 1.25rem;
    background-color: #ffffff;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    border-radius: 0.5rem;
    font-size: 1rem;

    &__title {
        margin-bottom: 1rem;
    }
}

.popup__footer {
    display: flex;
    flex-direction: column;
    gap: 1.2rem;

    &_input {
        outline: none;
    }
}
</style>
  