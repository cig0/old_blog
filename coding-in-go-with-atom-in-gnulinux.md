Coding in Go with Atom editor on GNU+Linux

Today I will be sharing a workaround I implemented to make third-party Go packages work with an standard Atom editor installation.

Lately I started to flirt with [Atom](https://atom.io "A hackable text editor for the 21st Century") after my boss suggested me to give it a try for working with our Puppet infrastructure implementation - thanks for the tip Adam!

Truth is that I have tried Atom in the past when it was at its early stages and while I saw at the time the project had a lot of potential there were too many issues, mainly related to performance, that pushed me away of it thus missing the opportunity to give it a fair try - for the record, I'm an avid Emacs user and lately a [Spacemacs](http://spacemacs.org "A community-driven Emacs distribution - The best editor is neither Emacs nor Vim, it's Emacs *and* Vim!") fan, more on it on an upcoming post. 

Time went on and now Atom is a quite mature and feature-complete text editor. While it's difficult for me to digest the idea that it is in fact a Chromium-based web browser tweaked to work as a text editor, and nontheless how bloated it "has" to be given its foundations and regardless all the work being done to optimize its performance, I can understand why the developers went this way: given its roots I suppose that most of them if not the vast majority are web-oriented developers, so to them this is a natural direction. Now, to be truthful, Atom 1.3.2 on my Fedora 23 system *runs incredible snappy*.

Atom has a big community that continuously adds new features in the form of plugins. As with other programming languages there are some Go packages that can (and will) make a difference at the moment of diving into the editor to start hammering the keyboard. 

So far I found these two third-party packages very useful:

* **go-config**: detects installed Go runtime(s), tools and configurations making them available for use by other packages
* **go-plus**: adds 'gocode', 'gofmt', 'goimports', 'go vet', 'golint', 'go build' and 'go test' functionality for the Go language


They both install well, but making them work is a different story.

---
####  Making Go packages work *without* launching Atom from the command line

<div style="text-align:center">
![The good days...](/home/@i90rr/Pictures/compu/Go/jumbo_gopher-4bf98fbc72cc188289ba2b458d4ce680.png)
<div style="text-align:left">

Tags: go, atom, spacemacs, programming, editor
