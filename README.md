# hunklosjriwah
public class NewtonRaphson {
    // Define the function f(x)
    public static double f(double x) {
        return x * x * x - 2 * x * x + 3 * x - 5;
    }

    // Define the derivative f'(x)
    public static double df(double x) {
        return 3 * x * x - 4 * x + 3;
    }

    public static void main(String[] args) {
        double x0 = 2.0; // initial guess
        double tolerance = 1e-6;
        int maxIterations = 100;

        double x = x0;
        for (int i = 0; i < maxIterations; i++) {
            double fx = f(x);
            double dfx = df(x);
            if (dfx == 0) break; // avoid division by zero
            double x1 = x - fx / dfx;

            if (Math.abs(x1 - x) < tolerance) {
                System.out.println("Root found: " + x1);
                return;
            }
            x = x1;
        }

        System.out.println("Root approximation: " + x);
    }
}
