<script setup lang="ts">
import { ref, computed } from 'vue'

// Kurslar ma'lumotlari
interface Course {
    id: number
    name: string
    category: string
    price: number
    duration: string
    rating: number
    students: number
}

const courses: Course[] = [
    { id: 1, name: 'Vue.js Boshlang\'ich Kurs', category: 'frontend', price: 99, duration: '2 oy', rating: 4.8, students: 1500 },
    { id: 2, name: 'React Advanced Dasturlash', category: 'frontend', price: 149, duration: '3 oy', rating: 4.9, students: 1200 },
    { id: 3, name: 'Node.js Backend Kursi', category: 'backend', price: 199, duration: '4 oy', rating: 4.7, students: 800 },
    { id: 4, name: 'Python Django Full Stack', category: 'backend', price: 129, duration: '3 oy', rating: 4.6, students: 950 },
    { id: 5, name: 'UI/UX Dizayn Asoslari', category: 'design', price: 89, duration: '2 oy', rating: 4.5, students: 1100 },
    { id: 6, name: 'JavaScript Mukammal Kurs', category: 'frontend', price: 79, duration: '2.5 oy', rating: 4.8, students: 2000 },
    { id: 7, name: 'Flutter Mobile Dasturlash', category: 'mobile', price: 179, duration: '3.5 oy', rating: 4.7, students: 700 },
    { id: 8, name: 'GraphQL va Apollo', category: 'backend', price: 119, duration: '2 oy', rating: 4.9, students: 600 }
]


const categories = [
    { value: '', label: 'Барча категориялар' },
    { value: 'frontend', label: 'Frontend' },
    { value: 'backend', label: 'Backend' },
    { value: 'mobile', label: 'Mobile' },
    { value: 'design', label: 'Dizayn' }
]

const filters = ref({
    category: '',
    search: ''
})

const filteredCourses = computed(() => {
    let result = courses

    if (filters.value.category) {
        result = result.filter(course => course.category === filters.value.category)
    }

    if (filters.value.search) {
        const searchLower = filters.value.search.toLowerCase()
        result = result.filter(course =>
            course.name.toLowerCase().includes(searchLower)
        )
    }

    return result
})

const isDropdownOpen = ref(true)
const selectedCourse = ref<Course | null>(null)

const selectCourse = (course: Course) => {
    selectedCourse.value = course
    isDropdownOpen.value = false
    filters.value.search = ''
}
</script>

<template>
    <div class="content-header">
        <h2>Направления курсов</h2>
        <hr />
    </div>
    <div class="courses-dropdown-container">
        <h3>Выбор курсов</h3>

        <div class="dropdown-wrapper">
            <div
                class="dropdown-trigger"
                :class="{ 'dropdown-open': isDropdownOpen }"
                @click="isDropdownOpen = !isDropdownOpen"
            >
                <div class="trigger-content">
          <span v-if="selectedCourse" class="selected-course">
            {{ selectedCourse.name }}
          </span>
                    <span v-else class="placeholder">
            Курсни танланг
          </span>
                </div>
                <span class="dropdown-arrow">▼</span>
            </div>

            <div v-show="isDropdownOpen" class="dropdown-menu">
                <!-- Filter qismi -->
                <div class="dropdown-filters">
                    <div class="filter-group">
                        <label>Категория:</label>
                        <select v-model="filters.category" class="filter-select">
                            <option
                                v-for="category in categories"
                                :key="category.value"
                                :value="category.value"
                            >
                                {{ category.label }}
                            </option>
                        </select>
                    </div>

                    <div class="filter-group">
                        <label>Қидириш:</label>
                        <input
                            v-model="filters.search"
                            type="text"
                            placeholder="Курс номини киритинг..."
                            class="search-input"
                        >
                    </div>
                </div>

                <div class="courses-list">
                    <div
                        v-for="course in filteredCourses"
                        :key="course.id"
                        class="course-item"
                        :class="{ 'selected': selectedCourse?.id === course.id }"
                        @click="selectCourse(course)"
                    >
                        <div class="course-info">
                            <h4 class="course-name">{{ course.name }}</h4>
                            <div class="course-details">
                                <span class="category">{{ course.category }}</span>
                                <span class="duration">{{ course.duration }}</span>
                                <span class="price">${{ course.price }}</span>
                            </div>
                            <div class="course-stats">
                                <span class="rating">⭐ {{ course.rating }}</span>
                                <span class="students">👥 {{ course.students }}</span>
                            </div>
                        </div>
                    </div>

                    <div v-if="filteredCourses.length === 0" class="no-courses">
                        💡 Курслар топилмади
                    </div>
                </div>
            </div>
        </div>

        <div v-if="selectedCourse" class="selected-course-info">
            <h3>Танланган курс:</h3>
            <div class="course-card">
                <h4>{{ selectedCourse.name }}</h4>
                <div class="card-details">
                    <p><strong>Категория:</strong> {{ selectedCourse.category }}</p>
                    <p><strong>Давомлилик:</strong> {{ selectedCourse.duration }}</p>
                    <p><strong>Нарх:</strong> ${{ selectedCourse.price }}</p>
                    <p><strong>Рейтинг:</strong> ⭐ {{ selectedCourse.rating }}</p>
                    <p><strong>Ўкувчилар:</strong> 👥 {{ selectedCourse.students }}</p>
                </div>
                <button class="enroll-btn">Курсга ёзилиш</button>
            </div>
        </div>
    </div>
</template>

<style scoped>
.courses-dropdown-container {
    width: 600px;
    height: 600px;
    margin: 2rem auto;
    padding: 2rem;
    font-family: Arial, sans-serif;
}

h2 {
    text-align: center;
    color: #2d3748;
    margin-bottom: 2rem;
    font-weight: bold;
}

/* Dropdown wrapper */
.dropdown-wrapper {
    position: relative;
    margin-bottom: 2rem;
}

/* Dropdown trigger */
.dropdown-trigger {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 1.5rem;
    border: 2px solid #e2e8f0;
    border-radius: 12px;
    background: white;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.dropdown-trigger:hover {
    border-color: #cbd5e0;
    box-shadow: 0 4px 6px rgba(0,0,0,0.1);
}

.dropdown-trigger.dropdown-open {
    border-color: #4299e1;
    box-shadow: 0 0 0 3px rgba(66, 153, 225, 0.1);
}

.trigger-content {
    flex: 1;
}

.selected-course {
    font-weight: 600;
    color: #2d3748;
}

.placeholder {
    color: #a0aec0;
}

.dropdown-arrow {
    transition: transform 0.3s ease;
    color: #718096;
}

.dropdown-trigger.dropdown-open .dropdown-arrow {
    transform: rotate(180deg);
}

/* Dropdown menu */
.dropdown-menu {
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    background: white;
    border: 1px solid #e2e8f0;
    border-radius: 12px;
    box-shadow: 0 10px 25px rgba(0,0,0,0.15);
    z-index: 1000;
    margin-top: 0.5rem;
    max-height: 400px;
    overflow: hidden;
    display: flex;
    flex-direction: column;
}

/* Filter qismi */
.dropdown-filters {
    padding: 1rem;
    background: #f7fafc;
    border-bottom: 1px solid #e2e8f0;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
}

.filter-group {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
}

.filter-group label {
    font-size: 0.875rem;
    font-weight: 600;
    color: #4a5568;
}

.filter-select, .search-input {
    padding: 0.5rem;
    border: 1px solid #cbd5e0;
    border-radius: 6px;
    font-size: 0.875rem;
}

.search-input:focus {
    outline: none;
    border-color: #4299e1;
}

/* Kurslar ro'yxati */
.courses-list {
    flex: 1;
    overflow-y: auto;
    max-height: 300px;
}

.course-item {
    padding: 1rem;
    border-bottom: 1px solid #f7fafc;
    cursor: pointer;
    transition: background-color 0.2s ease;
}

.course-item:hover {
    background-color: #f7fafc;
}

.course-item.selected {
    background-color: #ebf8ff;
    border-left: 4px solid #4299e1;
}

.course-name {
    margin: 0 0 0.5rem 0;
    color: #2d3748;
    font-size: 1rem;
}

.course-details {
    display: flex;
    gap: 1rem;
    margin-bottom: 0.5rem;
    font-size: 0.875rem;
}

.category, .duration, .price {
    padding: 0.25rem 0.5rem;
    border-radius: 4px;
    font-weight: 500;
}

.category {
    background: #fed7d7;
    color: #c53030;
}

.duration {
    background: #e9d8fd;
    color: #6b46c1;
}

.price {
    background: #c6f6d5;
    color: #276749;
}

.course-stats {
    display: flex;
    gap: 1rem;
    font-size: 0.875rem;
    color: #718096;
}

.no-courses {
    padding: 2rem;
    text-align: center;
    color: #a0aec0;
    font-style: italic;
}

.selected-course-info {
    background: #f7fafc;
    padding: 1.5rem;
    border-radius: 12px;
    border-left: 4px solid #4299e1;
}

.course-card h4 {
    margin: 0 0 1rem 0;
    color: #2d3748;
}

.card-details p {
    margin: 0.5rem 0;
    color: #4a5568;
}

.enroll-btn {
    background: #4299e1;
    color: white;
    border: none;
    padding: 0.75rem 1.5rem;
    border-radius: 6px;
    cursor: pointer;
    font-weight: 600;
    margin-top: 1rem;
    transition: background-color 0.2s ease;
}

.enroll-btn:hover {
    background: #3182ce;
}

/* Responsive design */
@media (max-width: 768px) {
    .dropdown-filters {
        grid-template-columns: 1fr;
    }

    .course-details {
        flex-direction: column;
        gap: 0.5rem;
    }
}
</style>