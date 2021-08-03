How did we managed to get so much styles files

1. we had big style.scss and style.css
2. create a folder 'styles'
3. rename styles.scss into main.scss and put it in
4. divide all other files into 2 folders:
  - blocks (common block styles)
  - utils (work files - vars, functions, mixins, placeholders)
5. In utils folder:
  5.1 create _variables.scss and put there all variables from main.scss
  5.2 create _functions.scss
  5.3 create _mixins.scss
  5.4 create _extends.scss for placeholders (something that we can extend)
6. In blocks folder:
  6.1 create title.scss and put there styles for block .title
  6.2 create game.scss and put there styles for block .game (all other styles)
      because all of our styles consider one block - .game block.

PUT IT ALL TOGETHER
7. connect blocks folder in main 
  7.1 in main.scss we type @use './blocks/title.scss';
      to use classes from title.scss
  7.2 @use './blocks/game.scss';
8. connect utils folder same way? 
  NO
  8.1 We write every other utils file into game.scss and title.scss
        (IF those vars/mixins used in that file)
      WITH needed path ('../utils/_mixins')
      AND changing every mention of util
        f.e.: 
          Before: @include .square($cell-size);
          After: @include mixins.square($cell-size);
        and
          Before: top: getShift($base-shift, $cell-size, $index);
          After: top: functions.getShift($base-shift, $cell-size, $index);
  8.2 for variables (too much of them) we use command:
        "@use '../utils/_variables' as *"
  8.3 for % or placeholders we don't need to put special directory,
      so just put it right
      "@use '../utils/_extends'"
9. do that to every block
10. reconnect main.scss into style.css with command
    "sass ./styles/main.scss styles.css --watch"

11. PROBLEM WITH "/" IN _variables
    "Using / for division is deprecated and will be removed in Dart Sass 2.0.0."

12. Continue



