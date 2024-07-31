import numpy as np
import matplotlib.pyplot as plt
import matplotlib.animation as animation
from scipy.optimize import line_search

def objective_function(x):
    return (x[0] - 7)**2 + (x[1] - 2)**2

def gradient(x):
    return np.array([2 * (x[0] - 7), 2 * (x[1] - 2)])

def steepest_descent_with_line_search(f, grad, x0, tolerance=1e-6, max_iterations=1000):
    x = x0
    history = [x0]
    for i in range(max_iterations):
        gradient_value = grad(x)
        # Use line search to find the optimal step size
        alpha = line_search(f, grad, x, -gradient_value)[0]
        if alpha is None:  # Fall back to a small step if line search fails
            alpha = 1e-4
        x_new = x - alpha * gradient_value
        history.append(x_new)
        if np.linalg.norm(x_new - x) < tolerance:
            break
        x = x_new
    return x, history

# Initial guess
x0 = np.array([9.0, 4.0])

# Perform the steepest descent method with line search
optimal_solution, history = steepest_descent_with_line_search(objective_function, gradient, x0)

# Extract x1 and x2 history for plotting
history = np.array(history)
x1_history = history[:, 0]
x2_history = history[:, 1]

# Create a figure for plotting
fig, ax = plt.subplots(figsize=(10, 6))

# Define the grid for plotting the objective function
x1 = np.linspace(0, 10, 400)
x2 = np.linspace(0, 10, 400)
x1, x2 = np.meshgrid(x1, x2)
z = objective_function([x1, x2])

# Plot the contour of the objective function
contour = ax.contour(x1, x2, z, levels=50, cmap='viridis')
fig.colorbar(contour)

# Plot setup for the path
line, = ax.plot([], [], 'o-', label='Steepest Descent Path')
optimal_point, = ax.plot(7, 2, 'r*', markersize=15, label='Optimal Solution (7, 2)')
ax.legend()
ax.set_xlabel('x1')
ax.set_ylabel('x2')
ax.set_title('Steepest Descent Path with Line Search on Objective Function Contour')
ax.grid()

# Function to initialize the plot
def init():
    line.set_data([], [])
    return line,

# Function to update the plot
def update(frame):
    line.set_data(x1_history[:frame], x2_history[:frame])
    return line,

# Create the animation
ani = animation.FuncAnimation(fig, update, frames=len(x1_history), init_func=init, blit=True)

# Save the animation as a video
ani.save('steepest_descent_with_line_search.mp4', writer='ffmpeg', fps=2)

plt.show()

print("Optimal solution:", optimal_solution)
print("Objective function value at optimal solution:", objective_function(optimal_solution))
