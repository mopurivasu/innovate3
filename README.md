import javafx.application.Application;
import javafx.collections.FXCollections;
import javafx.collections.ObservableList;
import javafx.scene.Scene;
import javafx.scene.chart.BarChart;
import javafx.scene.chart.CategoryAxis;
import javafx.scene.chart.NumberAxis;
import javafx.scene.chart.XYChart;
import javafx.scene.layout.VBox;
import javafx.stage.Stage;

public class DataVisualizationApp extends Application {

    @Override
    public void start(Stage primaryStage) {
        // Create data
        ObservableList<XYChart.Data<String, Number>> data = FXCollections.observableArrayList(
                new XYChart.Data<>("Category 1", 20),
                new XYChart.Data<>("Category 2", 30),
                new XYChart.Data<>("Category 3", 10),
                new XYChart.Data<>("Category 4", 40)
        );

        // Create a series
        XYChart.Series<String, Number> series = new XYChart.Series<>();
        series.setName("Data Series");
        series.setData(data);

        // Create a bar chart
        CategoryAxis xAxis = new CategoryAxis();
        NumberAxis yAxis = new NumberAxis();
        BarChart<String, Number> barChart = new BarChart<>(xAxis, yAxis);
        barChart.setTitle("Data Visualization");
        barChart.getData().add(series);

        // Create layout and scene
        VBox vbox = new VBox(barChart);
        Scene scene = new Scene(vbox, 800, 600);

        // Set stage properties
        primaryStage.setTitle("Data Visualization App");
        primaryStage.setScene(scene);
        primaryStage.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
}
