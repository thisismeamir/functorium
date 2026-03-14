### Overview of Numerical Grids in NRPy+

In this section, we will explore the concept of numerical grids in NRPy+, a Python library for solving partial differential equations (PDEs).

### Theory Review

#### Introduction to Numerical Grids**

A numerical grid is a discrete representation of a continuous space or domain. It is used to discretize the solution of PDEs by dividing the domain into smaller, manageable pieces called cells.

```python
# Import necessary libraries
import nrpy
```

### Code Implementation


```python
# Define a function to create a numerical grid
def create_numerical_grid(dx, dy, nx, ny):
    # Calculate the number of cells in each direction
    ncx = int(nx / dx)
    ncy = int(ny / dy)

    # Create the numerical grid
    grid = nrpy.create_grid(ncx, ncy)

    return grid

# Example usage:
dx = 0.01
dy = 0.01
nx = 100
ny = 100

grid = create_numerical_grid(dx, dy, nx, ny)
```

### Theory Review

#### Properties of Numerical Grids**

Numerical grids have several properties that make them useful for solving PDEs:

*   **Discretization**: Numerical grids discretize the solution space by dividing it into smaller cells.
*   **Spatial resolution**: The spatial resolution of a numerical grid determines the accuracy of the solution.

### Example Usage:


```python
# Print the number of cells in each direction
print("Number of cells in x-direction:", ncx)
print("Number of cells in y-direction:", ncy)

# Plot the numerical grid
import matplotlib.pyplot as plt

plt.imshow(grid, cmap='binary')
plt.show()
```

### Theory Review

#### Advantages of Using Numerical Grids**

Using numerical grids has several advantages:

*   **Improved accuracy**: Numerical grids can improve the accuracy of solutions by reducing the effect of truncation errors.
*   **Efficient computation**: Numerical grids can reduce computational costs by allowing for more efficient solution methods.

### Output


```python
# Print the output of the numerical grid
print(grid)
```

The output shows a 2D array representing the numerical grid, with each cell containing a value representing the solution at that point.**Author Information**
=====================

### Overview of Author Information

In this section, we will explore the information about the author of a document or publication.

### Theory Review

#### Introduction to Authorship**

An author is the person who creates and publishes written content, such as articles, books, or research papers. The author's name, affiliation, and contact information are typically included in the publication to provide credit for their work.

```python
# Define a dictionary with author information
author_info = {
    "name": "Zach Etienne",
    "affiliation": "University of Illinois at Urbana-Champaign",
    "email": "zetch@illinois.edu"
}
```

### Code Implementation


```python
# Print the author's name and affiliation
print("Author:", author_info["name"])
print("Affiliation:", author_info["affiliation"])

# Print the author's email address
print("Email:", author_info["email"])
```

### Theory Review

#### Properties of Authorship**

Authorship has several properties that make it important for academic and professional purposes:

*   **Credit**: Authors receive credit for their work, which can impact their reputation and career advancement.
*   **Accountability**: Authors are accountable for the accuracy and validity of their work.

### Example Usage:


```python
# Print a citation for the author's work
print("Citation:", "Z. Etienne (2022), Publication Title")
```

### Theory Review

#### Advantages of Authorship**

Authorship has several advantages, including:

*   **Personal satisfaction**: Authors can feel proud and satisfied with their contributions to a field.
*   **Professional recognition**: Authors may receive awards or recognition for their work.

### Output


```python
# Print the output of the author information
print("Author:", author_info["name"])
print("Affiliation:", author_info["affiliation"])
print("Email:", author_info["email"])
```

The output shows the author's name, affiliation, and email address, which can be used to provide credit for their work or contact them for further information.**NRPy+ Grid Module**
=====================

### Overview of NRPy+ Grid Module

In this section, we will explore the NRPy+ grid module, which provides a way to register grid functions in NRPy+, set basic parameters of a numerical grid, and provide functions for reading and writing grid functions to memory.

### Theory Review

#### Introduction to Numerical Grids**

Numerical grids are discrete representations of continuous spaces or domains. They are used to discretize the solution of partial differential equations (PDEs) by dividing the domain into smaller, manageable pieces called cells.

```python
# Import necessary libraries
import nrpy
```

### Code Implementation


```python
# Define a function to register grid functions in NRPy+
def register_grid_function(gridfunc):
    # Create a new grid function object
    grid_obj = nrpy.create_gridfunction(gridfunc)

    return grid_obj

# Example usage:
grid_func = "example_grid_func"
grid_obj = register_grid_function(grid_func)
```

### Theory Review

#### Properties of Numerical Grids**

Numerical grids have several properties that make them useful for solving PDEs:

*   **Discretization**: Numerical grids discretize the solution space by dividing it into smaller cells.
*   **Spatial resolution**: The spatial resolution of a numerical grid determines the accuracy of the solution.

### Parameters in NRPy+ Grid Module

The NRPy+ grid module has several parameters that can be set to customize its behavior:

*   **grid::DIM** -- the dimension of the grid (e.g., a 3D numerical grid will have grid::DIM=3).
*   **grid::Nx\[DIM\]** -- an integer array yielding the size of the grid in each direction.
*   **grid::MemAllocStyle** -- how the grid function is allocated in memory in the C code.

### Example Usage:


```python
# Set the dimension of the grid to 3
grid_dim = 3

# Set the size of the grid in each direction
nx = [100, 100, 100]

# Set the memory allocation style for the grid function
mem_alloc_style = "sequential"

# Create a new grid object with the specified parameters
grid_obj = nrpy.create_grid(grid_dim, nx, mem_alloc_style)
```

### Theory Review

#### Advantages of Using Numerical Grids**

Using numerical grids has several advantages:

*   **Improved accuracy**NRPy+ Grid Module**
=====================

### Overview of NRPy+ Grid Module

In this section, we will explore the NRPy+ grid module, which provides a way to register grid functions in NRPy+, set basic parameters of a numerical grid, and provide functions for reading and writing grid functions to memory.

### Theory Review

#### Introduction to Numerical Grids**

Numerical grids are discrete representations of continuous spaces or domains. They are used to discretize the solution of partial differential equations (PDEs) by dividing the domain into smaller, manageable pieces called cells.

```python
# Import necessary libraries
import nrpy
```

### Code Implementation


```python
# Define a function to register grid functions in NRPy+
def register_grid_function(gridfunc):
    # Create a new grid function object
    grid_obj = nrpy.create_gridfunction(gridfunc)

    return grid_obj

# Define a function to access grid function data in memory
def gfaccess(gfarrayname, varname, ijklstring):
    # Return the string to access the grid function in memory
    return f"{gfarrayname}[{ijklstring}]"

# Example usage:
grid_func = "example_grid_func"
grid_obj = register_grid_function(grid_func)

ijl_string = "i0,j0,k0"
gf_access_str = gfaccess("dummyGF", "CCTK_GFINDEX3D(cctkGH)", ijl_string)
```

### Theory Review

#### Properties of Numerical Grids**

Numerical grids have several properties that make them useful for solving PDEs:

*   **Discretization**: Numerical grids discretize the solution space by dividing it into smaller cells.
*   **Spatial resolution**: The spatial resolution of a numerical grid determines the accuracy of the solution.

### Parameters in NRPy+ Grid Module

The NRPy+ grid module has several parameters that can be set to customize its behavior:

*   **grid::DIM** -- the dimension of the grid (e.g., a 3D numerical grid will have grid::DIM=3).
*   **grid::Nx\[DIM\]** -- an integer array yielding the size of the grid in each direction.
*   **grid::MemAllocStyle** -- how the grid function is allocated in memory in the C code.

### Functions in NRPy+ Grid Module

The NRPy+ grid module provides several functions to help with reading and writing grid functions**NRPy+ Grid Function Definitions**
=====================================

### Overview of NRPy+ Grid Function Definitions

In this section, we will explore how NRPy+ generates human-friendly aliases for grid functions.

### Theory Review

#### Introduction to Grid Functions**

Grid functions are used to discretize the solution of partial differential equations (PDEs) by dividing the domain into smaller, manageable pieces called cells. They can be classified as either evolved or auxiliary quantities.

```python
# Import necessary libraries
import nrpy
```

### Code Implementation


```python
# Define a function to register grid functions in NRPy+
def register_grid_function(gridfuncs):
    # Create a new list of registered grid functions
    registered_gfs = []

    # Iterate over the grid functions
    for gf in gridfuncs:
        # Register the grid function with NRPy+
        nrpy.register_gridfunction(gf)

        # Add the grid function to the list of registered grid functions
        registered_gfs.append(gf)

    return registered_gfs

# Example usage:
grid_funcs = ["uu", "vv"]
registered_gfs = register_grid_function(grid_funcs)
```

### Theory Review

#### Properties of Grid Functions**

Grid functions have several properties that make them useful for solving PDEs:

*   **Evolved quantities**: Evolved grid functions represent the solution of the PDEs and are used to advance the solution in time.
*   **Auxiliary quantities**: Auxiliary grid functions are used to store additional information about the solution.

### Generating Human-Friendly Aliases

NRPy+ generates human-friendly aliases for grid functions by defining macros in `outdir/gridfunction_defines.h`. These macros can be used to access grid function values in C code.

```python
# Define a function to generate human-friendly aliases for grid functions
def generate_human_aliases(registered_gfs):
    # Create a new file to store the human-friendly aliases
    with open("outdir/gridfunction_defines.h", "w") as f:
        # Write the header comment
        f.write("#pragma once\n")
        f.write("// This file is automatically generated by NRPy+. Do not edit.\n")

        # Iterate over the registered grid functions
        for gf in registered_gfs:
            # Generate a human-friendly alias for the grid function
            human_alias = f"test_gfs[{gf}][IDX4(1,i0,i1,i2)]\n"
            f.write**Defining NUM_EVOL_GFS**
=========================

### Overview of Defining NUM_EVOL_GFS

In this section, we will explore how to define the `NUM_EVOL_GFS` variable in NRPy+.

### Theory Review

#### Introduction to Grid Functions**

Grid functions are used to discretize the solution of partial differential equations (PDEs) by dividing the domain into smaller, manageable pieces called cells. They can be classified as either evolved or auxiliary quantities.

```python
# Import necessary libraries
import nrpy
```

### Code Implementation


```python
# Define a variable to store the number of evolved grid functions
NUM_EVOL_GFS = 0

# Define a function to register grid functions in NRPy+
def register_grid_function(gridfuncs):
    global NUM_EVOL_GFS
    
    # Create a new list of registered grid functions
    registered_gfs = []

    # Iterate over the grid functions
    for gf in gridfuncs:
        # Register the grid function with NRPy+
        nrpy.register_gridfunction(gf)

        # Increment the number of evolved grid functions
        NUM_EVOL_GFS += 1

        # Add the grid function to the list of registered grid functions
        registered_gfs.append(gf)

    return registered_gfs

# Example usage:
grid_funcs = ["uu", "vv"]
registered_gfs = register_grid_function(grid_funcs)
```

### Theory Review

#### Properties of Grid Functions**

Grid functions have several properties that make them useful for solving PDEs:

*   **Evolved quantities**: Evolved grid functions represent the solution of the PDEs and are used to advance the solution in time.
*   **Auxiliary quantities**: Auxiliary grid functions are used to store additional information about the solution.

### Defining NUM_EVOL_GFS

The `NUM_EVOL_GFS` variable is defined as an integer that stores the number of evolved grid functions. This variable can be incremented whenever a new evolved grid function is registered with NRPy+.

```python
# Define the NUM_EVOL_GFS variable
NUM_EVOL_GFS = 2
```

### Output


```python
# Print the value of NUM_EVOL_GFS
print(NUM_EVOL_GFS)
```

The output will be `2`, indicating that there are 2 evolved grid functions registered with NRPy+.**Defining UUGF**
================

### Overview of Defining UUGF

In this section, we will explore how to define the `UUGF` variable in NRPy+.

### Theory Review

#### Introduction to Grid Functions**

Grid functions are used to discretize the solution of partial differential equations (PDEs) by dividing the domain into smaller, manageable pieces called cells. They can be classified as either evolved or auxiliary quantities.

```python
# Import necessary libraries
import nrpy
```

### Code Implementation


```python
# Define a variable to store the value of UUGF
UUGF = 0

# Define a function to register grid functions in NRPy+
def register_grid_function(gridfuncs):
    # Create a new list of registered grid functions
    registered_gfs = []

    # Iterate over the grid functions
    for gf in gridfuncs:
        # Register the grid function with NRPy+
        nrpy.register_gridfunction(gf)

        # Increment the value of UUGF
        UUGF += 1

        # Add the grid function to the list of registered grid functions
        registered_gfs.append(gf)

    return registered_gfs

# Example usage:
grid_funcs = ["uu", "vv"]
registered_gfs = register_grid_function(grid_funcs)
```

### Theory Review

#### Properties of Grid Functions**

Grid functions have several properties that make them useful for solving PDEs:

*   **Evolved quantities**: Evolved grid functions represent the solution of the PDEs and are used to advance the solution in time.
*   **Auxiliary quantities**: Auxiliary grid functions are used to store additional information about the solution.

### Defining UUGF

The `UUGF` variable is defined as an integer that stores the value of a specific grid function. In this case, we define `UUGF` to be 0, indicating that no grid functions have been registered yet.

```python
# Define the UUGF variable
UUGF = 0
```

### Output


```python
# Print the value of UUGF
print(UUGF)
```

The output will be `0`, indicating that no grid functions have been registered with NRPy+.

$$ UUGF = 0 $$**Defining VVGF**
================

### Overview of Defining VVGF

In this section, we will explore how to define the `VVGF` variable in NRPy+.

### Theory Review

#### Introduction to Grid Functions**

Grid functions are used to discretize the solution of partial differential equations (PDEs) by dividing the domain into smaller, manageable pieces called cells. They can be classified as either evolved or auxiliary quantities.

```python
# Import necessary libraries
import nrpy
```

### Code Implementation


```python
# Define a variable to store the value of VVGF
VVGF = 1

# Define a function to register grid functions in NRPy+
def register_grid_function(gridfuncs):
    # Create a new list of registered grid functions
    registered_gfs = []

    # Iterate over the grid functions
    for gf in gridfuncs:
        # Register the grid function with NRPy+
        nrpy.register_gridfunction(gf)

        # Increment the value of VVGF
        VVGF += 1

        # Add the grid function to the list of registered grid functions
        registered_gfs.append(gf)

    return registered_gfs

# Example usage:
grid_funcs = ["uu", "vv"]
registered_gfs = register_grid_function(grid_funcs)
```

### Theory Review

#### Properties of Grid Functions**

Grid functions have several properties that make them useful for solving PDEs:

*   **Evolved quantities**: Evolved grid functions represent the solution of the PDEs and are used to advance the solution in time.
*   **Auxiliary quantities**: Auxiliary grid functions are used to store additional information about the solution.

### Defining VVGF

The `VVGF` variable is defined as an integer that stores the value of a specific grid function. In this case, we define `VVGF` to be 1, indicating that one auxiliary grid function has been registered with NRPy+.

```python
# Define the VVGF variable
VVGF = 1
```

### Output


```python
# Print the value of VVGF
print(VVGF)
```

The output will be `1`, indicating that one auxiliary grid function has been registered with NRPy+.

$$ VVGF = 1 $$

This output is followed by a comment in the code, indicating that it is an auxiliary variable:

```python
/* AUXILIARY VARIABLES:**Defining NUM_AUX_GFS**
=========================

### Overview of Defining NUM_AUX_GFS

In this section, we will explore how to define the `NUM_AUX_GFS` variable in NRPy+.

### Theory Review

#### Introduction to Grid Functions**

Grid functions are used to discretize the solution of partial differential equations (PDEs) by dividing the domain into smaller, manageable pieces called cells. They can be classified as either evolved or auxiliary quantities.

```python
# Import necessary libraries
import nrpy
```

### Code Implementation


```python
# Define a variable to store the number of auxiliary grid functions
NUM_AUX_GFS = 0

# Define a function to register grid functions in NRPy+
def register_grid_function(gridfuncs):
    # Create a new list of registered grid functions
    registered_gfs = []

    # Iterate over the grid functions
    for gf in gridfuncs:
        # Register the grid function with NRPy+
        nrpy.register_gridfunction(gf)

        # Increment the number of auxiliary grid functions
        NUM_AUX_GFS += 1

        # Add the grid function to the list of registered grid functions
        registered_gfs.append(gf)

    return registered_gfs

# Example usage:
grid_funcs = ["uu", "vv"]
registered_gfs = register_grid_function(grid_funcs)
```

### Theory Review

#### Properties of Grid Functions**

Grid functions have several properties that make them useful for solving PDEs:

*   **Evolved quantities**: Evolved grid functions represent the solution of the PDEs and are used to advance the solution in time.
*   **Auxiliary quantities**: Auxiliary grid functions are used to store additional information about the solution.

### Defining NUM_AUX_GFS

The `NUM_AUX_GFS` variable is defined as an integer that stores the number of auxiliary grid functions. In this case, we define `NUM_AUX_GFS` to be 0, indicating that no auxiliary grid functions have been registered yet.

```python
# Define the NUM_AUX_GFS variable
NUM_AUX_GFS = 0
```

### Output


```python
# Print the value of NUM_AUX_GFS
print(NUM_AUX_GFS)
```

The output will be `0`, indicating that no auxiliary grid functions have been registered with NRPy+.

$$ NUM\_AUX\_GFS = 0 $$

This output is followed by a comment in the code**Defining NUM_AUXEVOL_GFS**
==========================

### Overview of Defining NUM_AUXEVOL_GFS

In this section, we will explore how to define the `NUM_AUXEVOL_GFS` variable in NRPy+.

### Theory Review

#### Introduction to Grid Functions**

Grid functions are used to discretize the solution of partial differential equations (PDEs) by dividing the domain into smaller, manageable pieces called cells. They can be classified as either evolved or auxiliary quantities.

```python
# Import necessary libraries
import nrpy
```

### Code Implementation


```python
# Define a variable to store the number of auxiliary-evolved grid functions
NUM_AUXEVOL_GFS = 0

# Define a function to register grid functions in NRPy+
def register_grid_function(gridfuncs):
    # Create a new list of registered grid functions
    registered_gfs = []

    # Iterate over the grid functions
    for gf in gridfuncs:
        # Register the grid function with NRPy+
        nrpy.register_gridfunction(gf)

        # Increment the number of auxiliary-evolved grid functions
        NUM_AUXEVOL_GFS += 1

        # Add the grid function to the list of registered grid functions
        registered_gfs.append(gf)

    return registered_gfs

# Example usage:
grid_funcs = ["phi"]
registered_gfs = register_grid_function(grid_funcs)
```

### Theory Review

#### Properties of Grid Functions**

Grid functions have several properties that make them useful for solving PDEs:

*   **Evolved quantities**: Evolved grid functions represent the solution of the PDEs and are used to advance the solution in time.
*   **Auxiliary-evolved quantities**: Auxiliary-evolved grid functions are used to store additional information about the solution.

### Defining NUM_AUXEVOL_GFS

The `NUM_AUXEVOL_GFS` variable is defined as an integer that stores the number of auxiliary-evolved grid functions. In this case, we define `NUM_AUXEVOL_GFS` to be 0, indicating that no auxiliary-evolved grid functions have been registered yet.

```python
# Define the NUM_AUXEVOL_GFS variable
NUM_AUXEVOL_GFS = 0
```

### Output


```python
# Print the value of NUM_AUXEVOL_GFS
print(NUM_AUXEVOL_GFS)
```

The output will be `1`, indicating that one auxiliary**Registering Gridfunction `phi`**
====================================

### Overview of Registering Gridfunctions**

In this section, we will explore how to register a gridfunction called `phi` in NRPy+.

### Theory Review

#### Introduction to Grid Functions**

Grid functions are used to discretize the solution of partial differential equations (PDEs) by dividing the domain into smaller, manageable pieces called cells. They can be classified as either evolved or auxiliary quantities.

```python
# Import necessary libraries
import nrpy
```

### Code Implementation


```python
# Register gridfunction phi as type "AUX"
nrpy.register_gridfunction("phi", gftype="AUX")
```

### Theory Review

#### Properties of Grid Functions**

Grid functions have several properties that make them useful for solving PDEs:

*   **Evolved quantities**: Evolved grid functions represent the solution of the PDEs and are used to advance the solution in time.
*   **Auxiliary quantities**: Auxiliary grid functions are used to store additional information about the solution.

### Registering Gridfunction `phi`

The `phi` gridfunction is registered with NRPy+ as an auxiliary quantity. This means that it will be used to store additional information about the solution, but not evolved in time.

```python
# Define phi as a SymPy variable
import sympy as sp

phi = sp.Function("phi")
```

### Accessing Gridfunction `phi` from Memory**

The `phi` gridfunction can be accessed from memory using its alias and index values. This is done by creating an `IDX4` string that specifies the index values of the grid function.

```python
# Create IDX4 string for accessing phi
ijkl_string = "i0,j0,k0"
phi_access_str = f"phi[{ijkl_string}]"
```

### Output


```python
# Print the value of phi_access_str
print(phi_access_str)
```

The output will be `phi[i0,j0,k0]`, indicating that the `phi` gridfunction can be accessed from memory using its alias and index values.

$$ \text{phi} = \text{Function}( " \text{phi}" ) $$**Registering Gridfunctions: Important Notes**
=============================================

### Overview of Registering Gridfunctions**

In this section, we will explore the important notes about registering gridfunctions in NRPy+.

### Theory Review

#### Introduction to Grid Functions**

Grid functions are used to discretize the solution of partial differential equations (PDEs) by dividing the domain into smaller, manageable pieces called cells. They can be classified as either evolved or auxiliary quantities.

```python
# Import necessary libraries
import nrpy
```

### Code Implementation


```python
# Register gridfunction phi as type "AUX"
try:
    nrpy.register_gridfunction("phi", gftype="AUX")
except Exception as e:
    print(f"Warning: {e}")
```

### Theory Review

#### Properties of Grid Functions**

Grid functions have several properties that make them useful for solving PDEs:

*   **Evolved quantities**: Evolved grid functions represent the solution of the PDEs and are used to advance the solution in time.
*   **Auxiliary quantities**: Auxiliary grid functions are used to store additional information about the solution.

### Registering Gridfunctions: Important Notes**

When registering gridfunctions with NRPy+, there are some important notes to keep in mind:

*   **Registering gridfunctions can only be run once on a given gridfunction**: Once a gridfunction is registered, it cannot be re-registered.
*   **Warning message will be printed if trying to re-register a gridfunction**:

```python
# Define phi as a SymPy variable
import sympy as sp

phi = sp.Function("phi")
```

### Accessing Gridfunction `phi` from Memory**

The `phi` gridfunction can be accessed from memory using its alias and index values. This is done by creating an `IDX4` string that specifies the index values of the grid function.

```python
# Create IDX4 string for accessing phi
ijkl_string = "i0,j0,k0"
phi_access_str = f"phi[{ijkl_string}]"
```

### Output


```python
# Print the value of phi_access_str
print(phi_access_str)
```

The output will be `phi[i0,j0,k0]`, indicating that the `phi` gridfunction can be accessed from memory using its alias and index values.

$$ \text{phi} = \text{Function}( " \text{phi}" ) $$

Note that if you**Registering Gridfunctions and Accessing them from Memory**
=============================================================

### Overview of Registering Gridfunctions**

In this section, we will explore how to register a gridfunction called `phi` in NRPy+.

### Theory Review

#### Introduction to Grid Functions**

Grid functions are used to discretize the solution of partial differential equations (PDEs) by dividing the domain into smaller, manageable pieces called cells. They can be classified as either evolved or auxiliary quantities.

```python
# Import necessary libraries
import nrpy
```

### Code Implementation


```python
# Register gridfunction phi as type "AUX"
phi = gri.register_gridfunctions("AUX", "phi")
```

### Theory Review

#### Properties of Grid Functions**

Grid functions have several properties that make them useful for solving PDEs:

*   **Evolved quantities**: Evolved grid functions represent the solution of the PDEs and are used to advance the solution in time.
*   **Auxiliary quantities**: Auxiliary grid functions are used to store additional information about the solution.

### Accessing Gridfunction `phi` from Memory**

The `phi` gridfunction can be accessed from memory using its alias and index values. This is done by creating an `IDX4` string that specifies the index values of the grid function.

```python
# Create IDX4 string for accessing phi
ijkl_string = "i0,j0,k0"
phi_access_str_senr = gri.gfaccess("in_gfs", "phi", ijkl_string)
```

### Setting Memory Access Parameters**

The memory access parameters can be set using the `set_paramsvals_value` function.

```python
# Set memory access parameter to ETK
par.set_paramsvals_value("grid::GridFuncMemAccess = ETK")
```

### Accessing Gridfunction `phi` from Memory with ETK**

The `phi` gridfunction can be accessed from memory using its alias and index values, with the ETK memory access.

```python
# Create IDX4 string for accessing phi with ETK
ijkl_string_etk = "i0,j0,k0"
phi_access_str_etk = gri.gfaccess("in_gfs", "phi", ijkl_string_etk)
```

### Output


```python
# Print the value of phi_access_str_senr and phi_access_str_etk
print(phi_access_str_senr)
print(phi_access_str_etk)
```

The output will be**Working with Gridfunctions**
==============================

### Overview of Working with Gridfunctions**

In this section, we will explore how to work with gridfunctions in NRPy+.

### Theory Review

#### Introduction to Grid Functions**

Grid functions are used to discretize the solution of partial differential equations (PDEs) by dividing the domain into smaller, manageable pieces called cells. They can be classified as either evolved or auxiliary quantities.

```python
# Import necessary libraries
import nrpy
```

### Code Implementation


```python
# Register gridfunction phi as type "AUX"
phi = gri.register_gridfunctions("AUX", "phi")
```

### Theory Review

#### Properties of Grid Functions**

Grid functions have several properties that make them useful for solving PDEs:

*   **Evolved quantities**: Evolved grid functions represent the solution of the PDEs and are used to advance the solution in time.
*   **Auxiliary quantities**: Auxiliary grid functions are used to store additional information about the solution.

### Working with Gridfunctions**

The `phi` gridfunction can be accessed from memory using its alias and index values. This is done by creating an `IDX4` string that specifies the index values of the grid function.

```python
# Create IDX4 string for accessing phi
ijkl_string = "i0,j0,k0"
phi_access_str_senr = gri.gfaccess("in_gfs", "phi", ijkl_string)
```

### Printing Square of `phi`**

The square of the `phi` gridfunction can be printed as a regular SymPy variable.

```python
# Print the square of phi
print(phi**2)
```

### Printing Type of `phi`**

The type of the `phi` gridfunction can be printed using the `variable_type()` function.

```python
# Print the type of phi
print(gri.variable_type(phi))
```

### Printing Lists of Registered Gridfunctions**

The lists of registered evolved, auxiliary, and aux-evolved variables can be printed using the `gridfunction_lists()` function.

```python
# Get lists of registered gridfunctions
evolved_variables_list,auxiliary_variables_list, auxevol_variables_list = gri.gridfunction_lists()[0:3]

# Print the lists
print(evolved_variables_list)
print(auxiliary_variables_list)
print(auxevol_variables_list)
```

### Output of `gridfunction_defines()`**

The output of the `grid**Defining NUM_EVOL_GFS**
=========================

### Overview of Defining NUM_EVOL_GFS**

In this section, we will explore how to define the `NUM_EVOL_GFS` variable in NRPy+.

### Theory Review

#### Introduction to Grid Functions**

Grid functions are used to discretize the solution of partial differential equations (PDEs) by dividing the domain into smaller, manageable pieces called cells. They can be classified as either evolved or auxiliary quantities.

```python
# Import necessary libraries
import nrpy
```

### Code Implementation


```python
# Define NUM_EVOL_GFS to 0
NUM_EVOL_GFS = 0

# Print the value of NUM_EVOL_GFS
print(NUM_EVOL_GFS)
```

### Theory Review

#### Properties of Grid Functions**

Grid functions have several properties that make them useful for solving PDEs:

*   **Evolved quantities**: Evolved grid functions represent the solution of the PDEs and are used to advance the solution in time.
*   **Auxiliary quantities**: Auxiliary grid functions are used to store additional information about the solution.

### Defining NUM_EVOL_GFS**

The `NUM_EVOL_GFS` variable is defined as an integer that stores the number of evolved grid functions. In this case, we define `NUM_EVOL_GFS` to be 0, indicating that no evolved grid functions have been registered yet.

```python
# Define the value of NUM_EVOL_GFS
NUM_EVOL_GFS = 0
```

### Output


```python
# Print the output of gridfunction_defines()
print("/* AUXILIARY VARIABLES: */")
```

The output will be `0`, indicating that no evolved grid functions have been registered with NRPy+. The `gridfunction_defines()` function is called, which prints the auxiliary variables.

$$ \text{NUM\_EVOL\_GFS} = 0 $$**Defining NUM_AUX_GFS**
=========================

### Overview of Defining NUM_AUX_GFS**

In this section, we will explore how to define the `NUM_AUX_GFS` variable in NRPy+.

### Theory Review

#### Introduction to Grid Functions**

Grid functions are used to discretize the solution of partial differential equations (PDEs) by dividing the domain into smaller, manageable pieces called cells. They can be classified as either evolved or auxiliary quantities.

```python
# Import necessary libraries
import nrpy
```

### Code Implementation


```python
# Define NUM_AUX_GFS to 1
NUM_AUX_GFS = 1

# Print the value of NUM_AUX_GFS
print(NUM_AUX_GFS)
```

### Theory Review

#### Properties of Grid Functions**

Grid functions have several properties that make them useful for solving PDEs:

*   **Evolved quantities**: Evolved grid functions represent the solution of the PDEs and are used to advance the solution in time.
*   **Auxiliary quantities**: Auxiliary grid functions are used to store additional information about the solution.

### Defining NUM_AUX_GFS**

The `NUM_AUX_GFS` variable is defined as an integer that stores the number of auxiliary grid functions. In this case, we define `NUM_AUX_GFS` to be 1, indicating that one auxiliary grid function has been registered yet.

```python
# Define the value of NUM_AUX_GFS
NUM_AUX_GFS = 1
```

### Output


```python
# Print the output of gridfunction_defines()
print("/* AUXILIARY VARIABLES: */")
print("// EVOLVED VARIABLES:")
print("// AUXEVOL VARIABLES:")
```

The output will be `1`, indicating that one auxiliary grid function has been registered with NRPy+. The `gridfunction_defines()` function is called, which prints the auxiliary and evolved variables.

$$ \text{NUM\_AUX\_GFS} = 1 $$**Defining PHIGF**
=================

### Overview of Defining PHIGF**

In this section, we will explore how to define the `PHIGF` variable in NRPy+.

### Theory Review

#### Introduction to Grid Functions**

Grid functions are used to discretize the solution of partial differential equations (PDEs) by dividing the domain into smaller, manageable pieces called cells. They can be classified as either evolved or auxiliary quantities.

```python
# Import necessary libraries
import nrpy
```

### Code Implementation


```python
# Define PHIGF to 0
PHIGF = 0

# Print the value of PHIGF
print(PHIGF)
```

### Theory Review

#### Properties of Grid Functions**

Grid functions have several properties that make them useful for solving PDEs:

*   **Evolved quantities**: Evolved grid functions represent the solution of the PDEs and are used to advance the solution in time.
*   **Auxiliary quantities**: Auxiliary grid functions are used to store additional information about the solution.

### Defining PHIGF**

The `PHIGF` variable is defined as an integer that stores a value associated with the grid function. In this case, we define `PHIGF` to be 0, indicating that no specific value has been assigned yet.

```python
# Define the value of PHIGF
PHIGF = 0
```

### Output


```python
# Print the output of gridfunction_defines()
print("// AUXILIARY VARIABLES:")
```

The output will be `0`, indicating that no specific value has been assigned to the grid function. The `gridfunction_defines()` function is called, which prints the auxiliary variables.

$$ \text{PHIGF} = 0 $$

Note that in NRPy+, `PHIGF` is used to access a grid function, and its value is not directly related to the grid function's properties or behavior.**Defining NUM_AUXEVOL_GFS**
==========================

### Overview of Defining NUM_AUXEVOL_GFS**

In this section, we will explore how to define the `NUM_AUXEVOL_GFS` variable in NRPy+.

### Theory Review

#### Introduction to Grid Functions**

Grid functions are used to discretize the solution of partial differential equations (PDEs) by dividing the domain into smaller, manageable pieces called cells. They can be classified as either evolved or auxiliary quantities.

```python
# Import necessary libraries
import nrpy
```

### Code Implementation


```python
# Define NUM_AUXEVOL_GFS to 0
NUM_AUXEVOL_GFS = 0

# Print the value of NUM_AUXEVOL_GFS
print(NUM_AUXEVOL_GFS)
```

### Theory Review

#### Properties of Grid Functions**

Grid functions have several properties that make them useful for solving PDEs:

*   **Evolved quantities**: Evolved grid functions represent the solution of the PDEs and are used to advance the solution in time.
*   **Auxiliary quantities**: Auxiliary grid functions are used to store additional information about the solution.

### Defining NUM_AUXEVOL_GFS**

The `NUM_AUXEVOL_GFS` variable is defined as an integer that stores the number of auxiliary-evolved grid functions. In this case, we define `NUM_AUXEVOL_GFS` to be 0, indicating that no auxiliary-evolved grid functions have been registered yet.

```python
# Define the value of NUM_AUXEVOL_GFS
NUM_AUXEVOL_GFS = 0
```

### Output


```python
# Print the output of gridfunction_defines()
print("// EXTERNAL VARIABLES:")
```

The output will be `0`, indicating that no auxiliary-evolved grid functions have been registered with NRPy+. The `gridfunction_defines()` function is called, which prints the external variables.

$$ \text{NUM\_AUXEVOL\_GFS} = 0 $$**Defining NUM_EXTERNAL_GFS**
==========================

### Overview of Defining NUM_EXTERNAL_GFS**

In this section, we will explore how to define the `NUM_EXTERNAL_GFS` variable in NRPy+.

### Theory Review

#### Introduction to Grid Functions**

Grid functions are used to discretize the solution of partial differential equations (PDEs) by dividing the domain into smaller, manageable pieces called cells. They can be classified as either evolved or auxiliary quantities.

```python
# Import necessary libraries
import nrpy
```

### Code Implementation


```python
# Define NUM_EXTERNAL_GFS to 0
NUM_EXTERNAL_GFS = 0

# Print the value of NUM_EXTERNAL_GFS
print(NUM_EXTERNAL_GFS)
```

### Theory Review

#### Properties of Grid Functions**

Grid functions have several properties that make them useful for solving PDEs:

*   **Evolved quantities**: Evolved grid functions represent the solution of the PDEs and are used to advance the solution in time.
*   **Auxiliary quantities**: Auxiliary grid functions are used to store additional information about the solution.

### Defining NUM_EXTERNAL_GFS**

The `NUM_EXTERNAL_GFS` variable is defined as an integer that stores the number of external grid functions. In this case, we define `NUM_EXTERNAL_GFS` to be 0, indicating that no external grid functions have been registered yet.

```python
# Define the value of NUM_EXTERNAL_GFS
NUM_EXTERNAL_GFS = 0
```

### Output


```python
# Print the output of gridfunction_defines()
print("// EXTERNAL VARIABLES:")
```

The output will be `0`, indicating that no external grid functions have been registered with NRPy+. The `gridfunction_defines()` function is called, which prints the external variables.

$$ \text{NUM\_EXTERNAL\_GFS} = 0 $$
