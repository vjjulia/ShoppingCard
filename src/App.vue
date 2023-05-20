<template>
  <body>    
    <main>
        <section class="items">
            <h4>Shopping Card</h4>
            <div class="product selected"
            v-for="makeup in makeup" :key="makeup" 
            >
                <div class="photo">
                    <img src={{makeup.image_link}}>
                </div>
                <div class="description"
                >
                    <span class="name">{{makeup.name}}</span>
                    <span class="price">{{makeup.price}}</span>
                    <div class="quantity-area">
                        <button>-</button>
                        <span class="quantity">1</span>
                        <button>+</button>
                    </div>
                </div>
            </div>
        </section>

        <section class="summary">
            <strong>Summary</strong>
            <table>
                <thead>
                    <tr>
                        <th>Item</th>
                        <th>Total</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>1x T-shirt</td>
                        <td>5.99</td>
                    </tr>
                    
                    <tr>
                        <th>Total</th>
                        <th>edd</th>
                    </tr>
                </tbody>
            </table>
        </section>
    </main>
</body>
</template>
<script>
export default {
    name: 'App',
    data() {
        return {
            makeup: {},

        }
    },
    created() {
        this.axios.get('http://makeup-api.herokuapp.com/api/v1/products.json?brand=covergirl&product_type=lipstick')
        .then((response) => {
            this.makeup = response.data

        })
    }
}
</script>
<style>
body {
  margin: 0;
  font-family: 'Open Sans', sans-serif;
}

main > section.items h4 {
  text-align: center;
  margin-top: 0;
  width: 100%;
}

main {
  display: flex;
  justify-content: center;
  align-items:flex-start;
  flex-wrap: wrap;
  padding-top: 20px;
}

main > section.items {
  display: flex;
  flex-direction: column;
  border: 1px solid lightgrey;
  padding: 20px;
  max-width: 500px;
  min-width: 300px;
  justify-content: center;
  
}

section.items .product {
  border: 1px solid lightgrey;
  margin: 6px;
  flex: 0 0 calc(33.333% - 24px);
  cursor: pointer;
  text-align: center;
}

section.items .product.selected {
  border: 2px solid rgb(29, 134, 233);

}

section.items .photo img {
    display: flex;
    max-width: 90px;
    padding: 10px;
}

section.items .description {
  display: flex;
  align-items: center;
  text-align: center;
  font-size: 11px;
  line-height: 15px;
  padding: 10px;
}

section.items  .description .price {
  font-weight: bold;
  margin: 4px auto;
}

section.items  .description .quantity-area {
  margin: 8px auto;
  height: 14px;
}

section.items  .description .quantity-area button {
  width: 16px;
  height: 16px;
  display: inline-flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}

section.items  .description .quantity-area .quantity {
  font-weight: bold;
  margin: 0 4px;
}


section.summary {
  background-color: rgb(245, 245, 245);
  padding: 20px;
  min-height: 200px;
  min-width: 200px;
  text-align: center;
}

section.summary table {
  width: 100%;
  padding-top: 12px;
  font-size: 11px;
  margin: auto;
}

section.summary table tbody tr:last-of-type th {
  border-top: 1px solid black;
  padding-top: 4px;
}

</style>
