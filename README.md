# EcoPlan-Optimizer

Creating a tool like EcoPlan-Optimizer involves several components, including data handling, cost calculations, carbon footprint estimation, and visualization. Below is a simplified implementation of such a program using Python. This script does not interact with real-world data but simulates some aspects of energy usage optimization. Please install the necessary packages if you haven't already.

```python
import numpy as np
import matplotlib.pyplot as plt

# Function to simulate energy usage data
def simulate_energy_usage(days=30):
    """
    Simulate energy usage for a specified number of days.
    Returns an array with daily energy usage in kWh.
    """
    np.random.seed(42)
    return np.random.uniform(low=10, high=50, size=days)  # Simulate daily energy usage between 10 and 50 kWh

# Function to calculate cost based on usage and price per kWh
def calculate_cost(energy_usage, price_per_kwh=0.12):
    """
    Calculate the total utility cost based on energy usage and price per kWh.
    """
    try:
        return energy_usage * price_per_kwh
    except Exception as e:
        print("Error calculating cost:", e)
        return None

# Function to estimate carbon footprint based on usage and emission factor
def calculate_carbon_footprint(energy_usage, emission_factor=0.45):
    """
    Estimate carbon footprint based on energy usage and emission factor.
    Emission factor is typically in kg CO2 per kWh.
    """
    try:
        return energy_usage * emission_factor
    except Exception as e:
        print("Error estimating carbon footprint:", e)
        return None

# Function to optimize energy usage
def optimize_energy_usage(energy_usage, reduction_factor=0.1):
    """
    Optimize energy usage by reducing it by a certain factor.
    """
    try:
        return energy_usage * (1 - reduction_factor)
    except Exception as e:
        print("Error optimizing energy usage:", e)
        return None

# Function to visualize the results
def visualize_results(original_usage, optimized_usage, costs, footprints):
    """
    Visualize the energy usage, costs, and carbon footprints before and after optimization.
    """
    try:
        days = np.arange(len(original_usage))
        
        plt.figure(figsize=(12, 8))
        
        # Plot energy usage
        plt.subplot(3, 1, 1)
        plt.plot(days, original_usage, label='Original Usage (kWh)')
        plt.plot(days, optimized_usage, label='Optimized Usage (kWh)')
        plt.xlabel('Day')
        plt.ylabel('Energy Usage (kWh)')
        plt.title('Energy Usage Optimization')
        plt.legend()
        
        # Plot costs
        plt.subplot(3, 1, 2)
        plt.plot(days, costs['original'], label='Original Cost ($)')
        plt.plot(days, costs['optimized'], label='Optimized Cost ($)')
        plt.xlabel('Day')
        plt.ylabel('Cost ($)')
        plt.title('Cost Reduction')
        plt.legend()
        
        # Plot carbon footprints
        plt.subplot(3, 1, 3)
        plt.plot(days, footprints['original'], label='Original Footprint (kg CO2)')
        plt.plot(days, footprints['optimized'], label='Optimized Footprint (kg CO2)')
        plt.xlabel('Day')
        plt.ylabel('Carbon Footprint (kg CO2)')
        plt.title('Carbon Footprint Reduction')
        plt.legend()
        
        plt.tight_layout()
        plt.show()
    
    except Exception as e:
        print("Error during visualization:", e)

def main():
    try:
        # Simulate energy usage
        original_usage = simulate_energy_usage()
        
        # Calculate costs and carbon footprints
        original_costs = calculate_cost(original_usage)
        original_footprints = calculate_carbon_footprint(original_usage)
        
        # Optimize energy usage
        optimized_usage = optimize_energy_usage(original_usage)
        
        # Calculate optimized costs and carbon footprints
        optimized_costs = calculate_cost(optimized_usage)
        optimized_footprints = calculate_carbon_footprint(optimized_usage)
        
        # Prepare data for plotting
        costs = {'original': original_costs, 'optimized': optimized_costs}
        footprints = {'original': original_footprints, 'optimized': optimized_footprints}
        
        # Visualize the results
        visualize_results(original_usage, optimized_usage, costs, footprints)
    
    except Exception as main_error:
        print("An error occurred in the main function:", main_error)

if __name__ == "__main__":
    main()
```

### Comments and Error Handling:

1. **Simulate Energy Usage:** A simple function to generate random daily energy usage within a predefined range.

2. **Calculate Cost and Footprint:** Functions calculate the total cost and estimated carbon emitted based on energy usage with basic exception handling.

3. **Optimize Energy Usage:** Simulates a reduction in energy usage to illustrate potential optimizations.

4. **Visualization:** Generates plots for the original and optimized energy usage, cost, and carbon footprints. Errors in plotting are caught and printed.

5. **Main Function:** Manages the entire workflow from simulation, calculation, optimization, and visualization with high-level exception handling.

This program provides an example structure. For real-world applications, you would integrate with authentic data sources and possibly use machine learning for more advanced optimizations.