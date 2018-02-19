class Store {
    constructor(name) {
         this.name = name;
         this.items = [];
         this.stock = {};
         this.prices = {};
         this.totalSales = 0;
    }

    isItemAvailable(name){
         var itemIndex = this.items.indexOf(name);
         if(itemIndex == -1){
              return false;
         }
         else {
             return true;
         }
    }

    getPrice(name){
         var isAvailable = this.isItemAvailable(name);
         if(isAvailable == true ){
              var price = this.prices[name];
              return price;
         }
         else {
             console.log("sorry we do not have", name);
         }
    }

    getTotalSale(){
       return this.totalSales;
    }

    sellItem(name, quantity){
         var available = this.stock[name];
         if(available < quantity){
              console.log("Sorry we do not have enough");
              return;
         }
         else {
             var itemPrice = this.getPrice(name);
             var currentSale = itemPrice * quantity;
             this.totalSales = this.totalSales + currentSale;
             var remaining = available - quantity;
             this.stock[name] = remaining;
               console.log("thanks for your purcase");
          }
      }

      addItem(name, quantity, price){
            var isExisting = this.isItemAvailable(name);
            if(isExisting == true){
                 var available = this.stock[name];
                  this.stock[name] = available + quantity;
           }
          else {
                 this.items.push(name);
                 this.prices[name] = price;
                 this.stock[name] = quantity;
          }
    }
}

var masbaStore = new Store("masba Fashion Store");
masbaStore.addItem("shirt", 40, 300);
masbaStore.addItem("pant", 20, 500);
masbaStore.isItemAvailable('juta')
