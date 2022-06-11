## Activate left window when the current one is closed in tmux

When I closed a window in tmux, it activates the window to the right of it. I want the last window to be activated. I could not find a setting for this but tmux has hooks for many events, so I set window-unlinked event to open the last-window. set-hook -g window-unlinked 'last-window'