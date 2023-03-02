# CSS Grid

#### `grid-template`

| Properties                                 | Note                                                  |
| ------------------------------------------ | ----------------------------------------------------- |
| grid-template-columns / grid-template-rows |                                                       |
| grid-template                              | grid-template-columns / grid-template-rows の省略形。 |
| grid-template-areas                        | エリアに名前をつける時の template 側。                |
| grid-auto-flow                             | implicit grid。                                       |
| auto-fit / auto-fll                        | repeat といっしょに使う。                             |

#### `grid-item`

| Properties                                                          | Note                                                                           |
| ------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| grid-column-start / grid-column-end / grid-row-start / grid-row-end |                                                                                |
| grid-column / grid-row                                              | grid-column-start / grid-column-end / grid-row-start / grid-row-end の省略形。 |
| grid-area                                                           | 紛らわしいが、これも、grid-column, grig-row の省略形                           |
| grid-area                                                           | さらに紛らわしいが、エリアに名前をつける時の item 側としても使う。             |

# grid-template

## 通常の指定の仕方

### grid-template-columns / grid-template-rows

```css
display: grid;
grid-template-columns: 1fr 1fr;
grid-template-rows: 1fr 2fr 1fr;
```

### grid-template

grid-template-columns / grid-template-rows の shorthand

```css
display: grid;

/* row -> column の順で指定する */
grid-template: 1fr 1fr 1fr 1fr / 1fr 1fr;
```

## 名前をつける

```css
display: grid;
grid-template-columns: [col1-start] 1fr [col1-end col2-start] 1fr [col2-end col3-start] 1fr [col3-end];
grid-template-rows: [row1-start] 1fr [row1-end row2-start] 1fr [row2-end];
```

## エリアを作る

```css
display: grid;

/* grid-template-areasだけではpx指定ができないので、 grid-template-columns / grid-template-rows と組み合わせて使う */
grid-template-columns: 1fr 150px;
grid-template-rows: 100px 1fr 100px;

/* 空のトラックを作りたい場合、. にする。 */
grid-template-areas:
  'navbar navbar'
  'main side'
  'footer .';
```

```css
.item-1 {
  grid-area: navbar;
}
.item-2 {
  grid-area: main;
}
.item-3 {
  grid-area: side;
}
.item-4 {
  grid-area: footer;
}
```

## grid-auto-flow \*implicit grid

```
2 * 4 = 8トラック準備している。
boxは5つあって、grid-auto-flow: column を指定すると、
縦方向に埋まっていく。

first   fifth
second
third
forth
```

```css
display: grid;
grid-template-columns: repeat(2, 1fr);
grid-template-rows: repeat(4, 1fr);
grid-auto-flow: column;
```

## auto-fit / auto-fll

auto-fit / auto-fit は repeat といっしょに使う。

```css
display: grid;
grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
```

# grid-item

## grid-column-start / grid-column-end / grid-row-start / grid-row-end

```css
grid-column-start: 3;
grid-row-start: 3;
grid-row-end: span 3;
```

## grid-column / grid-row

shorthand

```css
grid-column: 1 / 2;
grid-row: 4 / span 2;
```

## grid-area

紛らわしいが、grid-column, grig-row の shorthand

```css
.item-1 {
  /* row-start / column-start / row-end / column-end */
  grid-area: 4 / 2 / 6 / 5;
}
```
