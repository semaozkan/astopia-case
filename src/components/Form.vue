<template>
    <div class="rising-form">
        <form>
            <div class="form-grid">
                <div class="form-row">
                    <label>Full Name</label>
                    <input type="text" placeholder="Full Name" />
                </div>

                <div class="form-row">
                    <label>Gender</label>
                    <select>
                        <option class="option" disabled selected>Choose</option>
                        <option class="option" value="female">Kadın</option>
                        <option class="option" value="male">Erkek</option>
                        <option class="option" value="other">Diğer</option>
                    </select>
                </div>

                <div class="form-row">
                    <label>City</label>
                    <select v-model="selectedCity" id="city">
                        <option disabled value="">Choose</option>
                        <option v-for="city in cities" :key="city.id" :value="city.name" class="option">
                            {{ city.name }}
                        </option>
                    </select>
                </div>

                <div class="form-row">
                    <label>Email</label>
                    <input type="email" placeholder="abc@gmail.com" />
                </div>

                <div class="form-row custom-date-input">
                    <label for="date">Date of Birth</label>
                    <div class="date-display" @click="openDatePicker">
                        <span>{{ birthDate || 'Select' }}</span>
                        <img src="../assets/calendar-2.png" alt="calendar" class="calendar-icon" />
                    </div>

                    <input type="date" ref="realDateInput" v-model="birthDate" @change="updateDisplay"
                        class="hidden-date-input" />
                </div>


                <div class="time-of-birth">
                    <div class="form-row">
                        <label>Time of Birth</label>
                        <div class="time-group">
                            <select v-model="birthHour">
                                <option :value="''" disabled selected hidden></option>
                                <option v-for="hour in 24" :key="hour - 1" class="option">
                                    {{ hour - 1 < 10 ? '0' + (hour - 1) : hour - 1 }} </option>
                            </select>
                            :
                            <select v-model="birthMinute">
                                <option value="" disabled selected hidden></option>
                                <option v-for="hour in 60" :key="hour - 1" class="option">
                                    {{ hour - 1 < 10 ? '0' + (hour - 1) : hour - 1 }} </option>
                            </select>
                        </div>
                    </div>

                    <div class="checkbox-row box">
                        <input type="checkbox" id="assumeTime" v-model="assumeTime" />
                        <label for="assumeTime">I don’t know my time of birth assume 12:00 PM</label>
                    </div>
                </div>
            </div>

            <div class="form-footer">
                <button type="submit" class="submit-btn">Create Your Birth Chart</button>

                <div class="checkbox-row footer-box">
                    <input type="checkbox" id="consent" />
                    <label for="consent" class="checkbox-row-text">
                        I have read and accept the User Agreement. I consent to the use of my e-mail address for
                        marketing
                        and information purposes.
                    </label>
                </div>
            </div>


        </form>
    </div>
</template>

<script setup>
import { ref, watch, onMounted } from 'vue'

const cities = ref([])
const selectedCity = ref('')

const birthDate = ref('')
const realDateInput = ref(null)
const birthHour = ref(null)
const birthMinute = ref(null)
const assumeTime = ref(false)



function openDatePicker() {
    realDateInput.value.click()
}

function updateDisplay(event) {
    birthDate.value = event.target.value
}

onMounted(async () => {
    const res = await fetch('/locations.json')
    const data = await res.json()
    cities.value = data
})

watch(assumeTime, (newVal) => {
    if (newVal) {
        birthHour.value = 12
        birthMinute.value = '00'
    } else {
        birthHour.value = ''
        birthMinute.value = ''
    }
})

watch([birthHour, birthMinute], () => {
    console.log('Hour:', birthHour.value, 'Minute:', birthMinute.value)
})
</script>

<style scoped>
.rising-form {
    font-family: "Inter", sans-serif;
    background: url("../assets/form.png") no-repeat center center;
    background-size: cover;
    padding: 30px 20.5px;
    max-width: 724px;
    width: 100%;
    border-radius: 16px;
}

.rising-form form {
    display: flex;
    flex-direction: column;
}

.form-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 40px 50px;
    justify-content: space-between;
}

.form-row,
.time-of-birth {
    flex: 1 1 calc(50% - 25px);
    min-width: 240px;
    display: flex;
    flex-direction: column;
    gap: 6px;
}

.form-row label {
    font-size: 16px;
    font-weight: 500;
    line-height: 20px;
}

.form-row input,
.form-row select {
    padding: 10px 14px;
    border-radius: 8px;
    border: none;
    background-color: rgba(255, 255, 255, 0.1);
    font-size: 16px;
    line-height: 24px;
    box-shadow: 0px 0px 5px rgba(16, 24, 40, 0.25);
    width: 100%;
    box-sizing: border-box;
}

.form-row select {
    appearance: none;
    -webkit-appearance: none;
    -moz-appearance: none;
    background-image: url('../assets/arrow-down.png');
    background-repeat: no-repeat;
    background-position: right 14px center;
    background-size: 24px 24px;
    cursor: pointer;
}

.form-row ::placeholder,
select {
    color: rgba(255, 255, 255, 0.6);
}

.custom-date-input {
    position: relative;
}

.date-display {
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: rgba(255, 255, 255, 0.1);
    border-radius: 8px;
    padding: 10px 14px;
    font-size: 16px;
    box-shadow: 0px 0px 5px rgba(16, 24, 40, 0.25);
}

.date-display span {
    color: rgba(255, 255, 255, 0.6);
}

.calendar-icon {
    width: 23px;
    height: 23px;
}

.hidden-date-input {
    position: absolute;
    top: 0;
    left: 0;
    opacity: 0;
    width: 100%;
    height: 100%;
    cursor: pointer;
}

.time-group {
    display: flex;
    gap: 8px;
    align-items: center;
}

.time-group select {
    flex: 1;
}

.option {
    color: black;
}

.checkbox-row {
    display: flex;
    align-items: flex-start;
    gap: 4px;
    font-size: 12px;
}

.checkbox-row label {
    display: flex;
    gap: 8px;
    font-size: 10px;
    font-weight: 500;
    line-height: 20px;
    position: relative;
}

.checkbox-row label::before {
    content: "";
    display: inline-block;
    width: 12px;
    height: 12px;
    border-radius: 1.5px;
    background-color: #FBE1C4;
    border: 1px solid #ccc;
    margin-top: 4px;
    cursor: pointer;
    position: absolute;
    top: 0;
    left: -20px;
    box-sizing: border-box;
}

.checkbox-row input {
    display: none;
}

.checkbox-row input:checked+label::before {
    content: "✓";
    display: flex;
    align-items: center;
    justify-content: center;
    color: #00202F;
    font-size: 10px;
    text-align: center;
    line-height: 14px;
    font-weight: bold;
    position: absolute;
    top: 0;
    left: -20px;
}

.box {
    margin-left: 20px;
}

.form-footer {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 18px;
}

.submit-btn {
    font-family: "Poppins", sans-serif;
    padding: 12.64px 55.12px;
    color: rgba(16, 32, 66, 1);
    font-size: 16px;
    font-weight: 600;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    margin-top: 56px;
    background: linear-gradient(90deg, #FDEBCF 0%, #FEDBA0 100%);
    box-shadow:
        0px 2px 2px rgba(0, 0, 0, 0.25),
        inset 2px 2px 2px rgba(249, 251, 252, 0.4);
    cursor: pointer;
}

.footer-box {
    padding-left: 24px;
}

.checkbox-row-text {
    max-width: 400px;
    font-size: 12px;
    font-weight: 500;
    line-height: 20px;
    text-align: start;
}

@media (max-width: 992px) {
    .rising-form {
        margin: 0 auto;

    }
}

@media (max-width: 768px) {
    .rising-form {
        margin: 12px auto;
    }

    .form-grid {
        flex-direction: column;
    }

    .form-row,
    .time-of-birth {
        flex: 1 1 100%;
    }

    .time-group {
        flex-direction: row;
    }

    .checkbox-row {
        flex-direction: row;
    }
}
</style>