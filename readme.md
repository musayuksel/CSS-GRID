
<img src="https://res.cloudinary.com/wesbos/image/upload/v1515524452/GRID-social-share_wlfzk3.png" alt="css grid" width="400"/>

# CSS Grid 


## Properties for the Parent(grid container)


- **display:**
  ```css
  .container {
    display: grid | inline-grid;
  }
  ```

  - *grid*: generates a block-level grid
  - *inline-grid:* generates an inline-level grid

<hr>

- **grid-template-columns/grid-template-rows:**
  ```css
  .container {
    grid-template-columns: 1fr 1fr | minmax(10px, 1fr) 3fr | repeat(5, 1fr) | 50px auto 100px 1fr;
  }
  ```

  - *Grid lines* are automatically assigned positive numbers from these assignments (-1 being an alternate for the very last row).
  - But you can choose to explicitly name the *lines*. Note the bracket syntax for the line names:
  
  ```css
  .container {
    grid-template-columns: [first] 40px [line2] 50px [line3] auto [col4-start] 50px [five] 40px [end];
    grid-template-rows: [row1-start] 25% [row1-end] 100px [third-line] auto [last-line];
  }
  ```
<hr>

- **grid-template-areas:**
- Defines a grid template by referencing the names of the grid areas which are specified with the grid-area property.
  ```css
  .container {
      grid-template-areas: "<grid-area-name> | . | none | ...";
  }
  ```

  - *grid-area-name* the name of a grid area specified with grid-area.
  - **.** -a period signifies an empty grid cell.
  - *none:* no grid areas are defined.
 
    ```css
        .item-a {
            grid-area: header;
        }
        .item-b {
            grid-area: main;
        }
        .item-c {
            grid-area: sidebar;
        }
        .item-d {
            grid-area: footer;
        }

        .container {
            display: grid;
            grid-template-columns: 50px 50px 50px 50px;
            grid-template-rows: auto;
            grid-template-areas: 
                "header header header header"
                "main main . sidebar"
                "footer footer footer footer";
        }
    ```
<hr>

- **gap:** A shorthand for `row-gap` and `column-gap`
    ```css
    .container {
        gap: 15px 10px;
  }
  ```
<hr>

- **justify-items:** Aligns grid items along the row axis
    ```css
    .container {
        justify-items: start | end | center | stretch;
  }
  ```
  - *start:* – aligns items to be flush with the start edge of their cell
  - *end:* – aligns items to be flush with the end edge of their cell
  - *center:* – aligns items in the center of their cell
  - *stretch:* – fills the whole width of the cell (***default***)

<hr>

- **align-items:** Aligns grid items along the column axis
    ```css
    .container {
        align-items: start | end | center | baseline | stretch;
  }
  ```
  - *start:* – aligns items to be flush with the start edge of their cell
  - *end:* – aligns items to be flush with the end edge of their cell
  - *center:* – aligns items in the center of their cell
  - *baseline:* - align items along text baseline
  - *stretch:* – fills the whole height of the cell (***default***)

 <hr>

- **place-items:** sets both the `align-items` and `justify-items` properties in a single declaration.
    ```css
    .container {
        place-items: center;
  }
  ```
  - *align-items / justify-items:* – The first value sets `align-items`, the second value `justify-items`. If the second value is omitted, the first value is assigned to *both* properties.