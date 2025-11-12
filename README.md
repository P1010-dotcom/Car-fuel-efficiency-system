#include <stdio.h>
#include <string.h>

struct Car {
    int id;
    char name[50], brand[50];
    float mileage;
};

int main() {
    int n, i, j;
    struct Car temp;

    printf("Enter the number of cars: ");
    scanf("%d", &n);

    struct Car car[n];

    for (i = 0; i < n; i++) {
        printf("\nEnter details for Car %d:\n", i + 1);
        printf("Car ID: ");
        scanf("%d", &car[i].id);
        printf("Brand: ");
        scanf("%s", car[i].brand);
        printf("Model Name: ");
        scanf("%s", car[i].name);
        printf("Mileage (in km/l): ");
        scanf("%f", &car[i].mileage);
    }

    for (i = 0; i < n - 1; i++) {
        for (j = 0; j < n - i - 1; j++) {
            if (car[j].mileage < car[j + 1].mileage) {
                temp = car[j];
                car[j] = car[j + 1];
                car[j + 1] = temp;
            }
        }
    }

    printf("\n----------- CAR FUEL EFFICIENCY MANAGEMENT SYSTEM -----------\n");
    printf("Car Details Sorted by Mileage (Highest to Lowest):\n\n");
    printf("ID\tBrand\t\tModel\t\tMileage (km/l)\n");

    for (i = 0; i < n; i++) {
        printf("%d\t%-10s\t%-10s\t%.2f\n", car[i].id, car[i].brand, car[i].name, car[i].mileage);
    }

    return 0;
}
