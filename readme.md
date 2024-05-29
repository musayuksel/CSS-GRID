
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

<hr>

- **justify-content:** Sometimes the total size of your grid might be less than the size of its grid container- *if all of your grid items are sized with non-flexible units like `px`*. In this case you can set the alignment of the grid within the grid container.
    ```css
    .container {
      justify-content: start | end | center | stretch | space-around | space-between | space-evenly;    
  }
  ```
  - *start:* –  aligns the grid to be flush with the start edge of the grid container
  - *end:* – the end edge of the grid container
  - *center:* – aligns the grid in the center of the grid container
  - *stretch:* – resizes the grid items to allow the grid to fill the full width of the grid container
  - *space-around:* even amount of space between each grid item
  - *space-between:*
  - *space-evenly:*
<hr>

- **align-content:** Sometimes the total size of your grid might be less than the size of its grid container- *if all of your grid items are sized with non-flexible units like `px`*. In this case you can set the alignment of the grid within the grid container.
    ```css
    .container {
      align-content: start | end | center | stretch | space-around | space-between | space-evenly;    
  }
  ```
  - *similar to justify content*
<hr>

- **place-content:** sets both the `align-content` and `justify-content `properties in a single declaration.
  - The first value sets `align-content`, the second value `justify-content`. 
<hr>

- **grid-auto-columns/grid-auto-rows:** Specifies the size of any **auto-generated** grid tracks (aka *implicit grid tracks*). Implicit tracks get created **when there are more grid items than cells** in the grid or when a grid item is placed outside of the explicit grid. 
  ```css
    .container {
    grid-template-columns: 60px 60px;
    grid-template-rows: 90px 90px;
    grid-auto-columns: 60px;
  }
  ```
- all implicit columns will be `60px`

<hr>

- **grid-auto-flow** If you have grid items that you don’t explicitly place on the grid, the *auto-placement algorithm* kicks in to automatically place the items. This property ***controls how the auto-placement*** algorithm works.
  ```css
    .container {
      grid-auto-flow: row| column | row dense | column dense;
  }

   <div class="container">
      <div class="item">1</div>
      <div class="item">2</div>
      <div class="item">3</div>
      <div class="item">4</div>
      <div class="item">5</div>
    </div>
    <style>
      .container {
        display: grid;
        grid-template-columns: repeat(2, 100px);
        grid-template-rows: 200px 100px 400px;
        grid-gap: 20px;
        grid-auto-flow: column;
        <!-- 1 3 5-->
        <!-- 2 4  -->
      }
    </style>
  ```
  - *row*: default 
  - *column* – auto-placement algorithm fills each column in turn, adding new columns as necessary

