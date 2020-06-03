# Интерактивная таблица с использованием Vue.js


https://github.com/vagorobets

Основные требования к разработке:

  - Добавления/удаления новых строк таблицы;
  - Изменение уже добавленных строк;
  - Столбец рассчета полной стоимости; 
  - Использование vue.js

#### HTML
```sh
    <div id="app">
        <table>
            <tr>
                <th>Название</th>
                <th>Стоимость</th>
                <th>Количество</th>
                <th>Сумма</th>
                <th>Действие</th>
            </tr>
            <tr>
                <td> <input type="text" v-model="product" placeholder="Название" title = "Введите название"></td>
                <td><input type="number" v-model="price" placeholder="Стоимость" title = "Введите стоимость"></td>
                <td><input type="number" v-model="quantity" placeholder="Количество" title = "Введите количество"></td>
                <td class = 'grey'>{{ quantity * price }}</td>
                <td><button v-on:click="add" id="greenBtn">Добавить</button></td>
            </tr>
            <tr v-for="(product,index) in products">
                <td><input type="text" v-model="product.name" title = "Изменить наименование"></td>
                <td><input type="number" v-model="product.price" title = "Изменить стоимость"></td>
                <td><input type="number" v-model="product.quantity" title = "Изменить количество"></td>
                <td class = 'grey'>{{ product.price * product.quantity }}</td>
                <td><button v-on:click="products.splice(index, 1)" id="redBtn">Удалить</button></td>
            </tr>
        </table>
    </div>
```

#### CSS

```sh
 *{
        margin:  auto;
    }
    body {
        margin-top: 20px;
    }
    td{
        border: 1px solid black;
        width: 150px;
        text-align: center;
        font-style: italic;
    }
    input {
        outline: none;
        border: none;
        text-align: center;
        font-style: italic;
    }

    button{
        height: 30px;
        width: 100%;
        border: none;
    }
    .grey{
        background-color: rgb(223, 223, 223);
    }
    #greenBtn{
        background-color: #98FB98;
    }
    #greenBtn:hover, #greenBtn:active{
        background-color: #90EE90;
        outline: none;
    }
    #redBtn{
        background-color: #FA8072;
    }
    #redBtn:hover, #redBtn:active{
        background-color: #F08080;
        outline: none;
    }
```

#### Vue.js
```sh
new Vue({
            el: '#app',
            data: {
                products: [
                    {name: 'product3', price: 100, quantity: 4},
                    {name: 'product2', price: 200, quantity: 5},
                    {name: 'product1', price: 300, quantity: 6},
                ], 
                product: '',
                price: '',
                quantity: '',
            },
            methods: {
                add: function(){
                    if(this.product == '' || 
                       this.price == '' ||
                       this.quantity == ''){
                           alert('Введите недостающие значения')
                       } else {
                            let newObj = {
                                name: this.product, 
                                price: this.price,
                                quantity: this.quantity,
                            }
                            this.products.unshift(newObj);
                            this.product = '';
                            this.price = '';
                            this.quantity = '';
                       }
                },
            }
        });
```
