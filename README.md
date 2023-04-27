# Assignment Prog6221
##Code 
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Recipe_2
{
    class Program
    {

        static void Main(string[] args)
        {
            // Display current Foreground color
            //Console.WriteLine(Console.ForegroundColor);

            

            // Display current Foreground color
            //Console.WriteLine(Console.ForegroundColor);

            //Created a recipe object out of the class recipe
            //The methods will be called from the recipe object class
            Recipe recipe = new Recipe();
            while (true)
            {
                Console.WriteLine("===================================");
                // Set the Foreground color to blue
                Console.ForegroundColor
                    = ConsoleColor.Blue;
                Console.WriteLine("Enter '1' to enter recipe details");
                // Set the Foreground color to green
                Console.ForegroundColor
                    = ConsoleColor.Green;
                Console.WriteLine("Enter '2' to display recipe");
                // Set the Foreground color to magenta
                Console.ForegroundColor
                    = ConsoleColor.Magenta;
                Console.WriteLine("Enter '3' to scale recipe");
                // Set the Foreground color to yellow
                Console.ForegroundColor
                    = ConsoleColor.Yellow;
                Console.WriteLine("Enter '4' to reset quantities");
                // Set the Foreground color to cyan
                Console.ForegroundColor
                    = ConsoleColor.Cyan;
                Console.WriteLine("Enter '5' to clear recipe");
                // Set the Foreground color to red
                Console.ForegroundColor
                    = ConsoleColor.Red;
                Console.WriteLine("Enter '6' to exit");
                Console.WriteLine("===================================");

                Console.ResetColor();

                //These switch cases allow for the selection of each option
                string ans = Console.ReadLine();
                Console.WriteLine(" ");


                switch (ans)
                {

                    case "1" :
                        recipe.DetailEntry();
                        break;
                    case "2":
                        recipe.DisplayRecipe();
                        break;
                    case "3":
                        // Set the Foreground color to magenta
                        Console.ForegroundColor
                            = ConsoleColor.Magenta;
                        Console.Write("Enter scaling factor (0.5, 2, or 3): ");
                        double scale1;
                        if (double.TryParse(Console.ReadLine(), out scale1))
                        {
                            recipe.ScaleRecipe(scale1);
                        }
                        else
                        {
                            Console.WriteLine("\n+Please Enter a valid number+\n");
                        }
                        Console.ResetColor();
                        break;
                    case "4":
                        recipe.ResetQuantities();
                        break;
                    case "5":
                        recipe.ClearRecipe();
                        break;
                    case "6":
                        Environment.Exit(0);
                        break;
                    default:
                        Console.WriteLine("Invalid choice. Please enter a valid choice.");
                        break;
                }
            }
        }
    }

    //calculate all the requirements
    //methods = main statement
    class Recipe
    {
        private string[] ingredients;
        private double[] amount;
        private string[] units;
        private string[] steps;

        public Recipe()
        {
            // Initialize new user arrays for ingredients, quantities, units, steps
            ingredients = new string[0];
            amount = new double[0];
            units = new string[0];
            steps = new string[0];

        }

        public void DetailEntry()
        {

            // Set the Foreground color to blue
            Console.ForegroundColor
                = ConsoleColor.Blue;

            // Prompt the user to enter the number of ingredients

            Console.Write("Enter the number of ingredients: ");
            //If statement for error handling that will force the user to restart the program
            int ingNum;
            if (int.TryParse(Console.ReadLine(), out ingNum))
            {
                // Initialize the arrays with the correct size
                ingredients = new string[ingNum];
                amount = new double[ingNum];
                units = new string[ingNum];

                // Prompt the user to enter details for ingredient
                for (int i = 0; i < ingNum; i++)
                {
                    Console.WriteLine($"Enter details for ingredient #{i + 1}:");
                    Console.Write("Name: ");
                    ingredients[i] = Console.ReadLine();
                    Console.Write("Quantity: ");
                    amount[i] = double.Parse(Console.ReadLine());
                    Console.Write("Unit of measurement: ");
                    units[i] = Console.ReadLine();
                }

                // Prompt the user to enter number of steps
                Console.Write("Enter the number of steps: ");
                int Stnum = int.Parse(Console.ReadLine());

                // Initialize the steps array with the correct size
                steps = new string[Stnum];

                // Prompt the user to enter the details step
                for (int i = 0; i < Stnum; i++)
                {
                    Console.Write($"Enter step #{i + 1}: ");
                    steps[i] = Console.ReadLine();
                }

            }
            else
            {
                Console.WriteLine(" ");
                Console.WriteLine("Please Enter a number+\n");

            }


        }

        public void DisplayRecipe()
        {

            // Set the Foreground color to green
            Console.ForegroundColor
                = ConsoleColor.Green;

            // Display the ingredients and quantities
            Console.WriteLine("Ingredients:");
            for (int i = 0; i < ingredients.Length; i++)
            {
                Console.WriteLine($"- {amount[i]} {units[i]} of {ingredients[i]}");

            }

            // Display the steps
            Console.WriteLine("Steps:");
            for (int i = 0; i < steps.Length; i++)
            {
                Console.WriteLine($"- {steps[i]}");
            }
        }

        public void ScaleRecipe(double scale)
        {

            // Set the Foreground color to magenta
            Console.ForegroundColor
                = ConsoleColor.Magenta;

            // This will scale all our recipes by the scale we have chosen
            for (int i = 0; i < amount.Length; i++)
            {
                amount[i] *= scale;
            }
        }

        public void ResetQuantities()
        {

            // Set the Foreground color to yellow
            Console.ForegroundColor
                = ConsoleColor.Yellow;

            // Reset all the amounts to their original values
            for (int i = 0; i < amount.Length; i++)
            {
                amount[i] /= 2;
            }
        }

        public void ClearRecipe()
        {

            // Set the Foreground color to cyan
            Console.ForegroundColor
                = ConsoleColor.Cyan;

            // Reset all the arrays to empty
            ingredients = new string[0];
            amount = new double[0];
            units = new string[0];
            steps = new string[0];
        }
    }

}
