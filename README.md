import matplotlib.pyplot as plt

def bresenham(x1, y1, x2, y2):
    # List to store points on the line
    points = []

    # Calculate differences and error term
    dx = abs(x2 - x1)
    dy = abs(y2 - y1)
    sx = 1 if x1 < x2 else -1
    sy = 1 if y1 < y2 else -1
    err = dx - dy

    while True:
        # Append the current point to the list
        points.append((x1, y1))
        # Check if the end point is reached
        if x1 == x2 and y1 == y2:
            break
        e2 = 2 * err
        if e2 > -dy:
            err -= dy
            x1 += sx
        if e2 < dx:
            err += dx
            y1 += sy

    return points

def draw_line(x1, y1, x2, y2):
    # Get the points using Bresenham's algorithm
    line_points = bresenham(x1, y1, x2, y2)

    # Extract x and y coordinates
    x_coords, y_coords = zip(*line_points)

    # Plot the points
    plt.plot(x_coords, y_coords, marker='o', color='blue')
    plt.title("Bresenham's Line Drawing Algorithm")
    plt.xlabel('X-axis')
    plt.ylabel('Y-axis')
    plt.grid(True)
    plt.show()

# Define the endpoints
x1, y1 = 1, 1
x2, y2 = 5, 5

# Draw the line
draw_line(x1, y1, x2, y2)
