it provides some window management methods

![](https://user-images.githubusercontent.com/6236829/275310774-bbfece58-d92c-4ec8-b077-3498ee96471a.jpg)

## feature, limits
* implemented a 'tmux display-panes' UI
    * incompatible with &termguicolors
    * accept the imperfect highlight of winblend
    * no cursor hiding
    * stop working when a floatwin is being focused
    * no floatwin taking into account
* winjump: 1) by winnr 2) by display-panes
* winswap: 1) by winnr 2) by display-panes
* winzoom
* winresize

## prerequisite
* nvim 0.10.*
* tui nvim (due to infra.tty)
* haolian9/infra.nvim

## usage

here is my personal setting
```
do --winman
  ---@type winman.G
  local g = G("winman")
  g.display_panes_font = vim.go.background == "light" and "electronic" or "ansi_shadow"

  for i = 1, 9 do
    m.n("<leader>" .. i, function() require("winman.winjump").to(i) end)
  end
  m.n("<leader>0", function() require("winman.winjump").display_panes() end)

  m.n("<c-w>x", function() require("winman.winswap").display_panes() end)
  m.n("<c-w>z", function() require("winman.winzoom")() end)

  cmds.create("Resize", function() require("winman.winresize")() end)
end
```

## credits
* all the fonts used by this plugin come from http://patorjk.com/software/taag/
