<template>
    <div>
        <div class="modal fade" id="register_foundation" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
            <div class="modal-dialog">
                <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="exampleModalLabel">Registro fundación</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    
                    <AlertsForm :type_alert=" type_alert " :msg=" msg_alert"></AlertsForm>
                    <form method="post" action="url_link_donde_recibe datos">
                    <div class="mb-3">
                        <label for="recipient-name" class="col-form-label">Nombre:</label>
                        <input type="text" class="form-control" v-model="inputs.name">
                    </div>


                    <div class="mb-3">
                        <label for="recipient-name" class="col-form-label">Dirección:</label>
                        <input type="text" class="form-control" v-model="inputs.address">
                    </div>

                    <div class="mb-3">
                        <label for="recipient-name" class="col-form-label">Teléfono:</label>
                        <input type="text" class="form-control" v-model="inputs.phone">
                    </div>

                    <div class="mb-3">
                        <label for="recipient-name" class="col-form-label">Correo institucional:</label>
                        <input type="text" class="form-control" v-model="inputs.email">
                    </div>

                    <div class="mb-3">
                        <label for="recipient-name" class="col-form-label">Nombre de contacto:</label>
                        <input type="text" class="form-control" v-model="inputs.contact_name">
                    </div>

                    <div class="mb-3">
                        <label for="recipient-name" class="col-form-label">Apellido del contacto:</label>
                        <input type="text" class="form-control" v-model="inputs.contact_last_name">
                    </div>

                    <div class="mb-3">
                        <label for="recipient-name" class="col-form-label">Teléfono de contacto:</label>
                        <input type="text" class="form-control" v-model="inputs.contact_pone">
                    </div>

                    <div class="mb-3">
                        <label for="recipient-name" class="col-form-label">Correo de contacto:</label>
                        <input type="text" class="form-control" v-model="inputs.contact_email">
                    </div>

                    </form>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cancelar</button>
                    <button type="button" class="btn btn-primary" @click="save_register()">Registrar</button>
                </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import AlertsForm from '../general/AlertsForm.vue'


export default{
    name: 'ModalRegister',
    components:{
        AlertsForm
    },
    data(){
        return {
            inputs:{
                name: '',
                last_name: '',
                address: '',
                lat: '209384848',
                lng: '-12939.09899',
                phone: '',
                email: '',
                contact_name: '',
                contact_last_name: '',
                contact_pone: '',
                contact_email: ''
            },
            type_alert: '',
            msg_alert: ''
        }
    },
    methods:{
        async save_register(){
            console.log('llegaron los parametros', this.inputs)
            if(this.inputs.name == ''){
                this.type_alert = 'error'
                this.msg_alert= 'El campo nombre de fundación es requerido'
                console.log('El campo nombre de fundación es requerido');
                return;
            }

            if(this.inputs.address == ''){
                console.log('El campo dirección de fundación es requerido');
                this.type_alert = 'error'
                this.msg_alert= 'El campo dirección de fundación es requerido'
                return;
            }

            if(this.inputs.phone == ''){
                console.log('El campo telefono de fundación es requerido');
                this.type_alert = 'error'
                this.msg_alert= 'El campo teléfono de fundación es requerido'
                return;
            }

            if(this.inputs.email == ''){
                console.log('El campo correo de fundación es requerido');
                this.type_alert = 'error'
                this.msg_alert= 'El campo correo de fundación es requerido'
                return;
            }


            let url_api = '';

            const response = await fetch(url_api,{ 
                method: 'POST',
                headers:{
                    'Content-type': 'application/json'
                },
                body: JSON.stringify(this.inputs)
            });

            console.log('respuesta api', response)
        }

    }   
}
</script>