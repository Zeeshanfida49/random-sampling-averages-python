# random-sampling-averages-python
Lab task on random sampling, averages, and histogram visualization using Python.
# Random Sampling and Averages in Python

This project demonstrates how to work with **uniform random numbers, sample lists, averages, and histogram visualization** using Python.  
It combines multiple small tasks into a single workflow that is useful for simulations, probability experiments, and data analysis.

---

## 📌 Overview
The notebook contains the following functionalities:
- Generate random numbers uniformly distributed between two values.
- Create lists of random samples of any length.
- Compute the average of a list of numbers.
- Generate multiple random sample lists and calculate their averages.
- Visualize distributions of averages using **histograms** with `matplotlib`.

---

## 📂 Code Highlights

```python
import random
import matplotlib.pyplot as plt

# Generate a random number between a and b
def uniform_sample(a, b):
    return a + (b - a) * random.random()

# Create a list of n random samples
def create_samples_list(a, b, n):
    return [a + (b - a) * random.random() for _ in range(n)]

# Compute the average of a list
def average(numbers):
    if len(numbers) == 0:
        return None
    return sum(numbers) / len(numbers)

# Create m sample lists and their averages
def create_m_lists_and_averages(m, n, a, b):
    lists = [create_samples_list(a, b, n) for _ in range(m)]
    averages = [average(lst) for lst in lists]
    return lists, averages

# Generate averages for visualization
def create_averages(num_averages, list_size=10, a=1.0, b=2.0):
    averages = []
    for _ in range(num_averages):
        numbers = [a + (b - a) * random.random() for _ in range(list_size)]
        avg = sum(numbers) / len(numbers)
        averages.append(avg)
    return averages

# Plot histograms for different sample sizes
for num_averages in [100, 1000, 10000]:
    avg_list = create_averages(num_averages)
    plt.figure()
    plt.hist(avg_list, bins=50)
    plt.title(f"Histogram of {num_averages} averages (list size = 10)")
    plt.xlabel("Average value")
    plt.ylabel("Frequency")
    plt.show()

