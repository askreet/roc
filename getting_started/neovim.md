# Basic Neovim configuration for Roc

With [nvim-treesitter] installed, run:

    :TSInstall roc

Then for syntax highlighting, completion and diagnostics add the following
configuration to `init.lua` or similar. This assumes that roc nightly is
available in your PATH.

```lua
vim.api.nvim_create_autocmd({ "BufNewFile", "BufRead" }, {
	pattern = { "*.roc" },
	callback = function()
		vim.opt_local.filetype = "roc"

		vim.lsp.start({
			cmd = { "roc_language_server" },
			root_dir = vim.fn.getcwd(),
		})
	end,
})
```

[nvim-treesitter]: https://github.com/nvim-treesitter/nvim-treesitter
