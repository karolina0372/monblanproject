<template>
  <div class="date-filter">
    <div class="date-filter__label">Date</div>
    <div class="custom-datepicker-wrapper" data-input>
      <FlatPickr
        ref="startPicker"
        v-model="dateStart"
        :config="config"
        class="custom-datepicker"
        placeholder="from"
      />
      <div class="custom-datepicker-btns">
       <button class="custom-datepicker-btn custom-datepicker-btn__clear" @click="clearDate(startPicker, dateStart)"></button>
       <button class="custom-datepicker-btn custom-datepicker-btn__open" @click="openCalendar(startPicker)"></button>
      </div>
    </div>
    <div class="custom-datepicker-wrapper" data-input>
      <FlatPickr
        ref="endPicker"
        v-model="dateEnd"
        :config="config"
        class="custom-datepicker"
        placeholder="to"
      />
      <div class="custom-datepicker-btns">
       <button class="custom-datepicker-btn custom-datepicker-btn__clear" @click="clearDate(endPicker, dateEnd)"></button>
       <button class="custom-datepicker-btn custom-datepicker-btn__open" @click="openCalendar(endPicker)"></button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import FlatPickr from 'vue-flatpickr-component'
import 'flatpickr/dist/flatpickr.css'

const dateStart = ref(null);
const dateEnd = ref(null);
const startPicker = ref(null)
const endPicker = ref(null)

const config = {
  dateFormat: 'd_m_Y',
  maxDate: 'today',
  locale: {
    firstDayOfWeek: 7,
    weekdays: {
      shorthand: ['Su', 'Mo', 'Tu', 'We', 'Th', 'Fr', 'Sa'],
      longhand: ['Sunday',
        'Monday',
        'Tuesday',
        'Wednesday',
        'Thursday',
        'Friday',
        'Saturday']
    }
  },
  wrap: true,
};

const openCalendar = (pickerRef) => {
  pickerRef?.fp?.open()
}

const clearDate = (pickerRef) => {
  pickerRef?.fp?.clear()
}
</script>

<style lang="scss">
.date-filter {
  display: flex;
  align-items: center;
  margin-top: 20px;

  &__label {
    font-size: 16px;
    margin-right: 12px;
  }
}

.custom-datepicker {
  height: 28px;
  padding: 0 0 0 8px;
  border-radius: 4px;
  border: 1px solid #DEDEDE;
  font-size: 13px;
  font-family: 'Roboto', sans-serif;
  font-weight: 400;

  &:focus {
    outline: none;
  }
}

.custom-datepicker-wrapper {
  position: relative;
  display: flex;
  align-items: center;
  margin-right: 22px;
}

.custom-datepicker-btns {
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: center;
  right: 0;
  display: flex;
  height: 100%;
  background-color: #F4F4F4;
  border: 1px solid #DEDEDE;
  border-radius: 0 4px 4px 0;
}

.custom-datepicker-btn {
  width: 27px;
  height: 100%;
  border: none;
  cursor: pointer;
  background: center/24px no-repeat;

  &:hover {
    background-color: #E4E4E4;
  }

  &:active {
    background-color: #3D8EDA;
  }

  &__clear {
    background-image: url('@/assets/images/icon-close.png');
    border-right: 1px solid #DEDEDE;
  }

  &__open {
    background-image: url('@/assets/images/icon-calendar.png');
  }
}

.flatpickr-calendar {
  font-family: 'Roboto', sans-serif;
  border-radius: 5px;
  border: 1px solid #D2D1D2;
  box-shadow: 0 4px 4px rgba(0, 0, 0, 0.25);
}

span.flatpickr-weekday {
  font-family: 'Roboto', sans-serif;
  font-size: 13px;
  color: #000;
  font-weight: 700;
}

.flatpickr-day {
  border-radius: 2px;
  font-size: 13px;
  transition: all 0.2s;
  color: #333437;

  &:hover {
    background: #F4F4F4;
  }

  &.today {
    border: 1px solid #3D8EDA;

    &:hover {
      background: #3D8EDA;
      color: #fff;
    }
  }

  &.selected {
    background: #3D8EDA;
    color: #fff;
  }
}

.flatpickr-next-month,
.flatpickr-prev-month {
  position: relative;

  svg {
    display: none;
  }

  &:before {
    top: 0;
    left: 0;
    content: '';
    display: block;
    width: 14px;
    height: 14px;
    background: center/contain no-repeat;
  }
}

.flatpickr-prev-month::before {
  background-image: url('@/assets/images/icon-arrow-left.png');
}

.flatpickr-next-month::before {
  background-image: url('@/assets/images/icon-arrow-right.png');
}

@include screen(md) {
  .date-filter {
    flex-direction: column;
    align-items: stretch;
    gap: 6px;
  }

  .custom-datepicker-wrapper {
    margin-right: 0;
    max-width: 162px;
  }
}
</style>
