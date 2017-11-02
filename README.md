# Flash when hiding panels

If Vivaldi set as below configuration

<img src="https://github.com/WillyYu/vivaldi_1.11_toggle_panel/blob/master/images/vivaldi_layout_left_panel.png?raw=true" width="500"/>

The theme is Dark (background color is black) 
and tab strip is on the left and panels is set on right.

## Problem:
It looks flash when hiding the panel by commands or panel buttons.

## Root cause:
Why flash ?<br>
By Vivaldi's design, the layout is using flex and apply the alignment with "justify-content: flex-end" before hiding/showing animation. 
Which means the layout is align to right.<br>

During the hiding animation, the panel's width is getting small. <br>
But WebView is fixed width and align to right, which bring about moving to right.<br>
So the left side of Webview shows the background color. Like below screenshot: <br>

<img src="https://github.com/WillyYu/vivaldi_1.11_toggle_panel/blob/master/images/vivaldi_panel_hiding.png?raw=true" width="500" />

Util the animation is end, the webview's width re-layout and shown on full window.

Becuase the duration of animation is very short.<br>
It makes me feel uncomfortable. So I decide to fix it.<br>
This <a href="https://github.com/WillyYu/vivaldi_1.11_toggle_panel/commit/9dae724129db61f2bb22c6da13986226902da926">commit</a> is my solution
