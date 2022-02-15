## Commands  (space in a sheet)
- rename-sheet, guard-sheet
- open-plugins (a to activate, d to deactivate)

## Filtering and Sorting

  #  %  $  @  ~   => set column type to: numeric, float, currency, date, text
    z~    g$      => remove column type, set columns of selected rows to type
   `][     g[ g]`   => ascending/descending sort,  multiple (keyed) columns sort
    !      "      => id column as keyed, create sheet from selected rows
   s,u     t      => select/unselect a row, toggle a row
  gs,gu    gt     => select/unselect ALL rows, toggle ALL rows
    ,      g,     => select rows matching this column value, select rows that match on ANY column
   `|reg   \reg`    => select/unselect rows by regex
  `g|reg  g\reg`    => select/unselect ALL rows by regex
 `z|expr  z\expr`   => select/unselect rows by python expression (OPERATOR=="BUSINESS" and STATE=="FL")
 `z/expr  z?expr`   => search forward/backwards via python expression

## Editing and Saving

  Shift-V             => Visidata primary menu
  Shift-J   Shift-K   => Move row up/down by one
  Shift-H   Shift-L   => Move column left/right by one
   Ctrl-a    Ctrl-e   => move to beginning/end of line
   d   e   q   gq     => delete, rename, close sheet, close ALL sheets and quit
   `+`     ge#    z+    => add aggregator to column (check type #), replace values on selected rows, add aggregator to column (type correctly #)
   ^     g^    gz^    => edit column name, apply selected row column values to unnamed columns, apply row to ALL column values
   Ctrl+S      gY     => save data to a file, or copy to clipboard (pip tabulate allows saving as .github formatted tables)
   >>> print(tabulate(table, headers, tablefmt="fancy_grid"))

## Global

 Ctrl+r   O   U/R      => reload data, open Options sheet, undo/redo
 Shift-D      Ctrl+p   => open command log history, open messages history
 Shift-S  gS  Shift-C  => open "Sheets" sheet, sheets Graveyard,  Columns sheet
 Shift-F  gF  Shift-I  => create frequency table on one (or multiple keyed) columns, describe sheet stats

## Navigation

c+reg  zc+r  zr+n   => jump to column matching regex, jump to column/row number
  gj gk    gh gl    => to last/first row, leftmost/rightmost column
   / ?     g/ g?    => search column, search ALL columns
  Ctrl-^   Alt-#    => toggle between 2 sheets, switch to sheet num #
    _        g_     => auto fit column width, multiple column widths,
