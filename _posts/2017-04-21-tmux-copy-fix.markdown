---
layout: post
title:  "tmux copy fix"
date:   2017-04-21 16:23:22 +0100
categories: snippets
---

After updating tmux to 2.4 I got the problem with vi-copy. The error message was: `command not found: bind-key` 🤔

This fixed it:

**before:**
```
bind-key -t vi-copy 'v' begin-selection
bind-key -t vi-copy 'V' begin-selection
bind-key -t vi-copy 'y' copy-pipe "pbcopy" # for OSX
```

**now:**
```
bind-key -Tcopy-mode-vi 'v' send -X begin-selection
bind-key -Tcopy-mode-vi 'V' send -X begin-selection
bind-key -Tcopy-mode-vi 'y' send -X copy-pipe "pbcopy" # for OSX
```

Cheers!