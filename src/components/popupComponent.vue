<template>
    <div class="modal-shadow" @click.self="closePopup">
        <div class="popup">
            <div class="popup__header">
                <h3 class="popup__title">Выберите желаемое количество</h3>
            </div>
            <div class="popup__footer">
                <label for="btc"><input v-model="btc" type="number" min="0" @change="ConvertBtc" name="btc" class="">
                    Bitcoin</label>

                <label for="rub"><input v-model="rub" type="number" min="0" @change="ConvertRub" name="rub"
                        class="">Рубли</label>
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
}

@media screen and (max-width: 853px) {
    .header_submit_button {
        width: 100%;
    }

    .header_inputs {
        width: 100%;
    }
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
    padding: 1.25rem;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 20%;
    background: #ffffff;
    box-shadow: rgba(0, 0, 0, 0.7);
    z-index: 99;
    display: flex;
    flex-direction: column;
    height: 20%;
    border-radius: 0.4rem;
    display: flex;
    justify-content: space-between;
    height: auto;

    &body {
        overflow: hidden;
    }

    &__header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        flex: 0 0 auto;
        background-color: #ffffff;
    }

    &__content {
        display: flex;
        justify-content: space-between;
        align-items: center;
        background-color: #ffffff;
    }
}

.footer {
    display: flex;
    flex-direction: column;
    gap: 1.2rem;
}

.popup__close {
    cursor: pointer;
}

@media screen and (max-width: 853px) {
    .popup {
        width: 100%;
        height: 100%;
    }

    .modal-shadow {
        background: #ffffff;
    }
}
</style>
  