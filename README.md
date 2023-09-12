# CoffeeMachine
public class CoffeeMachine {
    private static final Scanner scanner = new Scanner(System.in);
    private static int water = 400;
    private static int milk = 540;
    private static int beans = 120;
    private static int cups = 9;
    private static int money = 550;

    public static void buy() {
        System.out.println("What do you want to buy? 1 - espresso, 2 - latte, 3 - cappuccino, back - to main menu: ");
        String choice = scanner.next();

        switch (choice) {
            case "1":
                makeCoffee(250, 0, 16, 4);
                break;

            case "2":
                makeCoffee(350, 75, 20, 7);
                break;

            case "3":
                makeCoffee(200, 100, 12, 6);
                break;

            case "back":
                break;

            default:
                break;
        }
    }

    public static void makeCoffee(int waterNeeded, int milkNeeded, int beansNeeded, int price) {
        if (water >= waterNeeded && milk >= milkNeeded && beans >= beansNeeded && cups >= 1) {
            System.out.println("I have enough resources, making you a coffee!");
            water -= waterNeeded;
            milk -= milkNeeded;
            beans -= beansNeeded;
            money += price;
            cups--;
        } else {
            System.out.println("Sorry, not enough resources!");
        }
    }

    public static void fill() {
        System.out.println("Write how many ml of water you want to add:");
        int addedWater = scanner.nextInt();
        System.out.println("Write how many ml of milk you want to add:");
        int addedMilk = scanner.nextInt();
        System.out.println("Write how many grams of coffee beans you want to add:");
        int addedBeans = scanner.nextInt();
        System.out.println("Write how many disposable cups you want to add:");
        int addedCups = scanner.nextInt();

        water += addedWater;
        milk += addedMilk;
        beans += addedBeans;
        cups += addedCups;
    }

    public static void take() {
        System.out.println("I gave you $" + money);
        money = 0;
    }

    public static void status() {
        System.out.println("The coffee machine has:");
        System.out.println(water + " ml of water");
        System.out.println(milk + " ml of milk");
        System.out.println(beans + " g of coffee beans");
        System.out.println(cups + " disposable cups");
        System.out.println("$" + money + " of money");
    }

    public static void main(String[] args) {
        while (true) {
            System.out.println("Write action (buy, fill, take, remaining, exit):");
            String action = scanner.next();

            switch (action) {
                case "buy":
                    buy();
                    break;

                case "fill":
                    fill();
                    break;

                case "take":
                    take();
                    break;

                case "remaining":
                    status();
                    break;

                case "exit":
                    return;

                default:
                    break;
            }
        }
    }
}
