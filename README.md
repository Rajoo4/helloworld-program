
import org.jsoup.Jsoup;
import org.jsoup.nodes.Document;
import org.jsoup.nodes.Element;
import org.jsoup.select.Elements;
import java.io.IOException;

public class AnimeSearch {
    public static void main(String[] args) {
        String searchQuery = "zoro";
        searchAnime(searchQuery);
    }

    private static void searchAnime(String query) {
        String url = "https://zorox.to/home" + query; // Replace with the actual URL

        try {
            Document document = Jsoup.connect(url).get();
            Elements results = document.select(".anime-title"); // Adjust the CSS selector based on the webpage structure

            if (results.isEmpty()) {
                System.out.println("No results found for " + query);
            } else {
                System.out.println("Results for " + query + ":");
                for (Element result : results) {
                    System.out.println(result.text());
                }
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
