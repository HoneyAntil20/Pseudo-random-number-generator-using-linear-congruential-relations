
This `README` will cover the project overview, key features, how to run the app, and details about the Linear Congruential Generator implementation.

````markdown
# ⚛️ Linear Congruential Playground

Visualize pseudo-random sequences, inspect their structure, and iterate on **Linear Congruential Generator (LCG)** parameters in real time. This interactive Streamlit application provides a simple yet powerful environment to explore the properties of one of the oldest and most well-known pseudo-random number generation algorithms.

---

## ✨ Features

* **Real-time Parameter Control:** Adjust the four key LCG parameters directly in the sidebar:
    * **Modulus ($m$)**: The cycle length.
    * **Multiplier ($a$)**: Controls the jump size.
    * **Increment ($c$)**: The shift amount.
    * **Seed ($X_0$)**: The starting value.
* **Sequence Generation:** Generate a sequence of a specified length instantly.
* **Step-by-Step Generation:** Use the "Next Value" button to append a single new number to the sequence, allowing for step-by-step analysis.
* **Statistical Analysis:** Key statistical metrics are calculated and displayed in vibrant cards:
    * **Count** (Sequence Length)
    * **Mean**
    * **Standard Deviation**
    * **Span** (Max - Min)
* **Sequence Visualization:** An interactive **Altair Area Chart** plots the normalized values over their index, making it easy to spot patterns, cycles, and lack of randomness.
* **Data Inspection & Export:** View the raw Integer and Normalized values in a table and download the complete dataset as a **CSV** file.
* **Custom Styling:** A custom CSS theme is applied for a modern and engaging user interface.

---

## ⚙️ How It Works

The application implements the **Linear Congruential Generator** using the formula:

$$
X_{n+1} = (aX_n + c) \pmod m
$$

Where:
* $X_{n+1}$ is the next pseudo-random integer.
* $X_n$ is the current integer.
* $a$ is the **multiplier**.
* $c$ is the **increment**.
* $m$ is the **modulus**.

The output is then **normalized** to a floating-point number between 0 and 1 by dividing the integer result by the modulus ($X_n / m$).

---

## 🚀 Getting Started

### Prerequisites

You need **Python** installed on your system.

### Installation

1.  **Clone the repository** (assuming your code is named `project.py`):
    ```bash
    git clone <your_repo_url>
    cd <your_repo_directory>
    ```

2.  **Install the required libraries** using pip:
    ```bash
    pip install streamlit pandas altair
    ```

### Running the App

Execute the application from your terminal using Streamlit:

```bash
streamlit run project.py
````

This command will open the app in your default web browser.

-----

## 💻 Code Structure

### `LinearCongruentialGenerator` Class

This class encapsulates the core logic of the LCG:

  * **`__init__(self, modulus, multiplier, increment, seed)`:** Initializes the generator with the LCG parameters and the starting `state` (seed).
  * **`reseed(self, seed)`:** Resets the generator's state to a new seed.
  * **`next_int(self)`:** Computes and returns the next pseudo-random **integer** based on the LCG formula.
  * **`next_float(self)`:** Returns the next pseudo-random **normalized float** (integer result divided by the modulus).

### `main()` Function

This is the Streamlit entry point, handling the following:

1.  **Initialization:** Sets up page configuration and CSS styling.
2.  **State Management:** Uses `st.session_state` to maintain the generator object, the generated sequence, and the application status across user interactions.
3.  **Sidebar UI:** Contains all the input widgets (`st.number_input`, `st.slider`, `st.button`) for parameter control and sequence generation.
4.  **Logic Handlers:** Functions like `refresh_generator` and `populate_sequence` manage the LCG state and sequence generation based on button clicks.
5.  **Main Content UI:** Displays the hero section, metric cards, the Altair visualization chart, and the sequence data table.

