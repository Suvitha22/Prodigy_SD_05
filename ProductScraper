import java.io.FileWriter;
import java.io.IOException;
import java.util.ArrayList;
import java.util.List;

import org.jsoup.Jsoup;
import org.jsoup.nodes.Document;
import org.jsoup.nodes.Element;
import org.jsoup.select.Elements;

import com.opencsv.CSVWriter;

public class ProductScraper {

    public static void main(String[] args) throws IOException {
        String targetUrl = "https://www.example.com/category/products"; // Replace with actual URL

        // Send request and parse HTML
        Document doc = Jsoup.connect(targetUrl).get();

        // Find product listings (replace with appropriate selectors)
        Elements productListings = doc.select("div.product-item");  // Adjust selector based on website

        // List to store product data
        List<Product> products = new ArrayList<>();

        // Extract product information and create Product objects
        for (Element productListing : productListings) {
            String name = productListing.select("h3.product-name").text().trim(); // Adjust selector
            String price = productListing.select("span.price").text().trim(); // Adjust selector
            String rating = productListing.select("span.rating").text().trim(); // Adjust selector (optional)

            products.add(new Product(name, price, rating));
        }

        // Write product data to CSV file
        writeToCsv(products);
        System.out.println("Product information scraped and saved to CSV file!");
    }

    private static void writeToCsv(List<Product> products) throws IOException {
        try (CSVWriter writer = new CSVWriter(new FileWriter("scraped_products.csv"))) {
            String[] header = {"Name", "Price", "Rating"}; // Adjust header names
            writer.writeNext(header);

            for (Product product : products) {
                String[] data = {product.getName(), product.getPrice(), product.getRating()};
                writer.writeNext(data);
            }
        }
    }
}

class Product {
    private String name;
    private String price;
    private String rating;

    public Product(String name, String price, String rating) {
        this.name = name;
        this.price = price;
        this.rating = rating;
    }

    // Getters and setters (optional)
}
