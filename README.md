# ShoppingCart
//Main class
java.util.*;
public class Main {
    public static void main(String[] args) {
        //TIP Press <shortcut actionId="ShowIntentionActions"/> with your caret at the highlighted text
        // to see how IntelliJ IDEA suggests fixing it.
        Scanner scanner = new Scanner(System.in);

        // Create some sample products
        Product tv = new Electronics("Smart Phone", 523, 65.99, 9, "Vivo", 12);
        Product shirt = new Clothing("Women's Top", 150, 15.99, 20, "M", "Cotton");

        // Add products to the shopping cart
        ShoppingCart cart = new ShoppingCart();
        cart.addToCart(tv);
        cart.addToCart(shirt);

        // Display cart contents and total price
        cart.displayCart();
        System.out.println("Total Price: $" + cart.calculateTotalPrice());

        scanner.close();
    }

    //Product class
    public class Product
{
    /**Create a `Product` Class:**
        - Implement a `Product` class with attributes `productName` (String), `productId` (int), `price` (double), and `quantityInStock` (int).
        - Include a method `displayDetails` to print details of the product.*/
    protected String productName;
    protected int productId;
    protected double price;
    protected int quantityInStock;
    public  Product(String productName, int productId, double price, int quantityInStock)
    {
        this.productName=productName;
        this.productId=productId;
        this.price=price;
        this.quantityInStock=quantityInStock;
    }

    public String getProductName() {
        return productName;
    }

    public void setProductName(String productName) {
        this.productName = productName;
    }

    public int getProductId() {
        return productId;
    }

    public void setProductId(int productId) {
        this.productId = productId;
    }

    public double getPrice() {
        return price;
    }

    public void setPrice(double price) {
        this.price = price;
    }

    public int getQuantityInStock() {
        return quantityInStock;
    }

    public void setQuantityInStock(int quantityInStock) {
        this.quantityInStock = quantityInStock;
    }

    public Product()
    {
        System.out.println("Add products:");
    }
    public void display()
    {
        System.out.println("Product Name: " + productName);
        System.out.println("Product ID: " + productId);
        System.out.println("Price: $" + price);
        System.out.println("Quantity in Stock: " + quantityInStock);
    }
}

//Electronics class
public class Electronics extends Product
{
    /* **Derived Classes - `Electronics` and `Clothing`:**
        - Create two classes, `Electronics` and `Clothing`, that inherit from the `Product` class.
        - Add attributes specific to each type (e.g., `brand` and `warrantyPeriod` for electronics, `size` and `material` for clothing).
        - Override the `displayDetails` method in each derived class to include information about the specific attributes.*/
    private String brand;
    private int warrantyPeriod;
    public Electronics()
    {
        System.out.println("Add Electronics:");
    }
    public Electronics(String productName, int productId, double price, int quantityInStock,String brand,int warrantyPeriod)
    {
        super(productName,productId,price,quantityInStock);
        this.brand=brand;
        this.warrantyPeriod=warrantyPeriod;
    }

    public String getBrand() {
        return brand;
    }

    public void setBrand(String brand) {
        this.brand = brand;
    }

    public int getWarrantyPeriod() {
        return warrantyPeriod;
    }

    public void setWarrantyPeriod(int warrantyPeriod) {
        this.warrantyPeriod = warrantyPeriod;
    }
    public void display()
    {
        System.out.println("Electronics Info : ");
        super.display();
        System.out.println("brand : "+brand);
        System.out.println("warrantyPeriod : "+warrantyPeriod);
    }
}

//clothing class
public class Clothing extends Product
{
    private String size;
    private String material;

    public Clothing(String productName, int productId, double price, int quantityInStock, String size, String material) {
        super(productName, productId, price, quantityInStock);
        this.size = size;
        this.material = material;
    }

    @Override
    public void display() {
        super.display();
        System.out.println("Size: " + size);
        System.out.println("Material: " + material);
    }
}

//Shopping cart
import java.util.ArrayList;
import java.util.List;
public class ShoppingCart
{
    private List<Product> cartItems;

    public ShoppingCart() {
        cartItems = new ArrayList<>();
    }

    public void addToCart(Product product) {
        cartItems.add(product);
        System.out.println("Product added to cart: " + product.getProductName());
    }
    public void displayCart() {
        if (cartItems.isEmpty()) {
            System.out.println("Your shopping cart is empty.");
        } else {
            System.out.println("Shopping Cart Contents:");
            for (Product item : cartItems) {
                item.display();
                System.out.println("*****");
            }
        }
    }
    public double calculateTotalPrice() {
        double total = 0;
        for (Product item : cartItems) {
            total += item.getPrice();
        }
        return total;
    }
}

