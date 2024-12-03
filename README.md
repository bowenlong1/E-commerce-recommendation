# Update the y-axis to display percentage format
import matplotlib.ticker as mticker

plt.figure(figsize=(12, 6))
plt.plot(df["Workload Date"], reductions, marker='o', label="Daily Workload Reduction", color='blue')
plt.axhline(mean_reduction, color='red', linestyle='--', label="Mean Reduction")
plt.axhline(ci_low, color='green', linestyle='--', label="95% CI Lower Bound")
plt.axhline(ci_high, color='green', linestyle='--', label="95% CI Upper Bound")

# Formatting
plt.title("Daily Workload Reduction with 95% Confidence Interval")
plt.xlabel("Workload Date")
plt.ylabel("Workload Reduction (%)")
plt.xticks(rotation=45)
plt.gca().yaxis.set_major_formatter(mticker.PercentFormatter(1.0))  # Format y-axis as percentage
plt.legend()
plt.grid(True)
plt.tight_layout()
plt.show()

