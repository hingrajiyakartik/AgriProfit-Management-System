#include <stdio.h>

int main(void)
{
    double land;
    double seed_qty, seed_price, seed_cost;
    double fertilizer_bags, fertilizer_price, fertilizer_cost;
    double pesticide_litres, pesticide_price, pesticide_cost;
    double extra_fertilizer_cost;
    double labour_per_vigha, labour_cost;
    double tractor_per_vigha, tractor_cost;
    double yield_per_vigha, total_yield, selling_price;
    double total_expenses, total_income, profit;

    printf("====================================\n");
    printf("   AGRICULTURE PROFIT CALCULATOR\n");
    printf("====================================\n");

    printf("Enter land in vigha: ");
    if (scanf("%lf", &land) != 1 || land <= 0)
    {
        printf("Error: Enter a valid land area.\n");
        return 1;
    }

    printf("\n--- SEED DETAILS ---\n");
    printf("Enter seed quantity in mann: ");
    if (scanf("%lf", &seed_qty) != 1 || seed_qty < 0)
        return 1;

    printf("Enter price per mann of seeds: ");
    if (scanf("%lf", &seed_price) != 1 || seed_price < 0)
        return 1;

    seed_cost = seed_qty * seed_price;

    printf("\n--- FERTILIZER DETAILS ---\n");
    printf("Enter number of fertilizer bags: ");
    if (scanf("%lf", &fertilizer_bags) != 1 ||
        fertilizer_bags < 0)
        return 1;

    printf("Enter price per fertilizer bag: ");
    if (scanf("%lf", &fertilizer_price) != 1 ||
        fertilizer_price < 0)
        return 1;

    fertilizer_cost = fertilizer_bags * fertilizer_price;

    printf("Enter additional fertilizer cost (Rs): ");
    if (scanf("%lf", &extra_fertilizer_cost) != 1 ||
        extra_fertilizer_cost < 0)
        return 1;

    printf("\n--- PESTICIDE DETAILS ---\n");
    printf("Enter pesticide quantity in litres: ");
    if (scanf("%lf", &pesticide_litres) != 1 ||
        pesticide_litres < 0)
        return 1;

    printf("Enter price per litre of pesticide: ");
    if (scanf("%lf", &pesticide_price) != 1 ||
        pesticide_price < 0)
        return 1;

    pesticide_cost = pesticide_litres * pesticide_price;

    printf("\n--- LABOUR AND TRACTOR COST ---\n");
    printf("Enter labour cost per vigha: ");
    if (scanf("%lf", &labour_per_vigha) != 1 ||
        labour_per_vigha < 0)
        return 1;

    labour_cost = land * labour_per_vigha;

    printf("Enter tractor cost per vigha: ");
    if (scanf("%lf", &tractor_per_vigha) != 1 ||
        tractor_per_vigha < 0)
        return 1;

    tractor_cost = land * tractor_per_vigha;

    printf("\n--- CROP SALES DETAILS ---\n");
    printf("Enter yield per vigha in mann: ");
    if (scanf("%lf", &yield_per_vigha) != 1 ||
        yield_per_vigha < 0)
        return 1;

    printf("Enter selling price per mann: ");
    if (scanf("%lf", &selling_price) != 1 ||
        selling_price < 0)
        return 1;

    total_yield = land * yield_per_vigha;

    total_expenses = seed_cost + fertilizer_cost
                   + extra_fertilizer_cost + pesticide_cost
                   + labour_cost + tractor_cost;

    total_income = total_yield * selling_price;
    profit = total_income - total_expenses;

    printf("\n====================================\n");
    printf("       FARMING REPORT\n");
    printf("====================================\n");

    printf("Land area             : %.2f vigha\n", land);
    printf("Seed expense          : Rs %.2f\n", seed_cost);
    printf("Fertilizer expense    : Rs %.2f\n", fertilizer_cost);
    printf("Extra fertilizer      : Rs %.2f\n",
           extra_fertilizer_cost);
    printf("Pesticide expense     : Rs %.2f\n", pesticide_cost);
    printf("Labour expense        : Rs %.2f\n", labour_cost);
    printf("Tractor expense       : Rs %.2f\n", tractor_cost);

    printf("------------------------------------\n");
    printf("Total expenses        : Rs %.2f\n", total_expenses);
    printf("Total crop yield      : %.2f mann\n", total_yield);
    printf("Total sales income    : Rs %.2f\n", total_income);
    printf("------------------------------------\n");

    if (profit > 0)
        printf("Net profit            : Rs %.2f\n", profit);
    else if (profit < 0)
        printf("Net loss              : Rs %.2f\n", -profit);
    else
        printf("Result                : No profit, no loss\n");

    printf("====================================\n");

    return 0;
}
