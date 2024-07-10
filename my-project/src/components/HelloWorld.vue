<template>
    <div class="container">
        <section class="articles">
            <h1>Статьи & Новости</h1>
            <div class="articles-grid">
                <div v-for="(article, index) in articles" :key="index" class="article-card">
                    <img :src="article.image" alt="Article Image" />
                    <div class="article-info">
                        <span class="category">{{ article.category }}</span>
                        <h3>{{ article.title }}</h3>
                        
                        <div class="button-flex"><p>{{ article.date }}</p> <button class="project-card-button"><img src="images/project-card-button.png" alt="button"></button></div>
                    </div>
                </div>
                
            </div>
        </section>
    
    <div class="pagination">
      <button v-for="page in totalPages" :key="page" @click="currentPage = page">{{ page }}</button>
    </div>
  
</div>
</template>

<script>
export default {
  data() {
    return {
      currentPage: 1,
      articlesPerPage: 6,
      articles: [
        {
          image: '/images/templateImage1.png',
          category: 'Дизайн Кухни',
          title: 'Создадим лучший макет перепланировки',
          date: '26 Декабрь, 2022'
        },
        {
          image: '/images/templateImage2.png',
          category: 'Дизайн Для Жизни',
          title: 'Лучшие интерьерные идеи по низкой цене',
          date: '22 Декабрь, 2022'
        },
        {
          image: '/images/templateImage3.png',
          category: 'Дизайн Интерьера',
          title: 'Лучшие интерьерные решения для офисов',
          date: '25 Декабрь, 2022'
        },
        {
          image: '/images/templateImage4.png',
          category: 'Дизайн Интерьера',
          title: 'Лучшие интерьерные решения для офисов',
          date: '25 Декабрь, 2022'
        },
        {
          image: '/images/templateImage5.png',
          category: 'Дизайн Интерьера',
          title: 'Лучшие интерьерные решения для офисов',
          date: '25 Декабрь, 2022'
        },
        {
          image: '/images/templateImage6.png',
          category: 'Дизайн Интерьера',
          title: 'Лучшие интерьерные решения для офисов',
          date: '25 Декабрь, 2022'
        },
      ]
    };
  },
  computed: {
    paginatedArticles() {
      const start = (this.currentPage - 1) * this.articlesPerPage;
      const end = start + this.articlesPerPage;
      return this.articles.slice(start, end);
    },
    totalPages() {
      return Math.ceil(this.articles.length / this.articlesPerPage);
    }
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=DM+Serif+Display&display=swap');

body {
    margin: 0;
    font-family: "DM Serif Display", serif;
}
  
.container {
    max-width: 1200px;
    margin: 0 auto;
  }

  .articles {
    text-align: center;
    margin-bottom: 40px;
}

.articles-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 27px;
    
}
  
.article-card {
    padding: 21px;
    box-shadow: 0px 10px 30px rgba(255, 255, 255, 0.25);
    border-radius: 62px;
    border: 1px #E7E7E7 solid;
    justify-content: flex-start;
    align-items: flex-start;
    gap: 10px;
}

.article-card img {
    width: 100%;
    height: auto;
}

.category {
    position: relative;
    width: 124px;
    height: 41px;
    left: 10px;
    bottom: 70px;
    background: white;
    border-top-left-radius: 8px;
    border-top-right-radius: 8px;
    border-bottom-right-radius: 8px;
    color: #4D5053;
    font-size: 16px;
    font-family: Jost;
    font-weight: 400;
    text-transform: capitalize;
    line-height: 24px;
    letter-spacing: 0.16px;
}

.article-info h3 {
    margin-top: 0;
    text-align: left;
    color: #292F36;
    font-size: 25px;
    font-family: DM Serif Display;
    font-weight: 400;
    line-height: 31.25px;
    letter-spacing: 0.50px;
    word-wrap: break-word;
}

.button-flex {
    display: flex;
    justify-content: space-between;
}

.project-card-button {
    width: 52px;
    height: 52px;
    left: 0px;
    top: 0px;
    border: none;
    background: #F4F0EC;
    border-radius: 9999px;
}

.pagination {
  margin-top: 20px;
}
.pagination button {
  margin-right: 5px;
  padding: 5px 10px;
}
</style>
