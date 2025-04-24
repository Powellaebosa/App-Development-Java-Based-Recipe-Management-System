
package recipe_test.java;
import java.util.ArrayList;
import java.util.Scanner;

public class Recipe {
    private String recipeName;
    private int servings;
    private final ArrayList<Ingredient> recipeIngredients;
    private int totalRecipeCalories;

    // Constructor that takes recipeName and servings as parameters
    public Recipe(String recipeName, int servings) {
        this.recipeName = recipeName;
        this.servings = servings;
        this.recipeIngredients = new ArrayList<>();
        this.totalRecipeCalories = 0;
    }

    // Accessor and mutator methods for recipeName
    public String getRecipeName() {
        return recipeName;
    }

    public void setRecipeName(String recipeName) {
        this.recipeName = recipeName;
    }

    // Accessor and mutator methods for servings
    public int getServings() {
        return servings;
    }

    public void setServings(int servings) {
        this.servings = servings;
    }

    // Accessor method for recipeIngredients
    public ArrayList<Ingredient> getRecipeIngredients() {
        return recipeIngredients;
    }

    // Accessor method for totalRecipeCalories
    public int getTotalRecipeCalories() {
        return totalRecipeCalories;
    }

    // Method to add an ingredient to the recipe
    public void addIngredient(Ingredient ingredient) {
        recipeIngredients.add(ingredient);
        totalRecipeCalories += ingredient.getCalories();
    }

    // Method to remove an ingredient from the recipe
    public void removeIngredient(Ingredient ingredient) {
        recipeIngredients.remove(ingredient);
        totalRecipeCalories -= ingredient.getCalories();
    }

    // Method to print the recipe
    public void printRecipe() {
        System.out.println(recipeName);
        System.out.println("Servings: " + servings);
        System.out.println("Ingredients:");

        recipeIngredients.forEach((ingredient) -> {
            System.out.println("- " + ingredient.getName() + ": " + ingredient.getAmount() + " " + ingredient.getUnit());
        });

        System.out.println("Total Calories: " + totalRecipeCalories);
    }

    // Method to create a new recipe from user input
    public static Recipe createNewRecipe() {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter recipe name:");
        String recipeName = scanner.nextLine();

        System.out.println("Enter serving size:");
        int servings = scanner.nextInt();

        Recipe recipe = new Recipe(recipeName, servings);

        System.out.println("Enter ingredients (one per line, with comma-separated name, amount, and unit):");

        scanner.nextLine(); // clear scanner buffer

        while (true) {
            String input = scanner.nextLine();

            if (input.isEmpty


