package com.recommender;

import org.apache.mahout.cf.taste.impl.model.file.FileDataModel;
import org.apache.mahout.cf.taste.impl.similarity.PearsonCorrelationSimilarity;
import org.apache.mahout.cf.taste.impl.neighborhood.NearestNUserNeighborhood;
import org.apache.mahout.cf.taste.impl.recommender.GenericUserBasedRecommender;
import org.apache.mahout.cf.taste.model.DataModel;
import org.apache.mahout.cf.taste.similarity.UserSimilarity;
import org.apache.mahout.cf.taste.neighborhood.UserNeighborhood;
import org.apache.mahout.cf.taste.recommender.Recommender;
import org.apache.mahout.cf.taste.recommender.RecommendedItem;

import java.io.File;
import java.util.List;

public class App {
    public static void main(String[] args) {
        try {
            File file = new File("src/main/resources/data.csv");
            System.out.println("File exists? " + file.exists());

            DataModel model = new FileDataModel(file);
            UserSimilarity similarity = new PearsonCorrelationSimilarity(model);
            UserNeighborhood neighborhood = new NearestNUserNeighborhood(2, similarity, model);
            Recommender recommender = new GenericUserBasedRecommender(model, neighborhood, similarity);

            List<RecommendedItem> recommendations = recommender.recommend(3, 3);

            System.out.println("Recommended items for user 3:");
            if (recommendations.isEmpty()) {
                System.out.println("No recommendations found.");
            } else {
                for (RecommendedItem item : recommendations) {
                    System.out.println("Item ID: " + item.getItemID() + " , Value: " + item.getValue());
                }
            }

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
