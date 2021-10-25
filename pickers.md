
217 => 70
129 (bin)

|                 |   FzfPreview   |      FzfLua     |    Telescope    | Best |     Description    |
|:---------------:|:--------------:|:---------------:|:---------------:|:----:|:------------------:|
|    bookmarks    |    Bookmarks   |       n/a       |    bookmarks    |  n/a |  chrome bookmarks  |
|     buffers     |  [All]Buffers  |     buffers     |     buffers     |  n/a |       buffers      |
|   buffer lines  |   BufferLines  |      blines     |       n/a       |  n/a |    buffer lines    |
|     changes     |     Changes    |       n/a       |       n/a       |  n/a |     change list    |
|     commands    |       n/a      |     commands    |     commands    |  n/a |    command list    |
| command history | CommandPalette | command_history | command_history |  n/a |   command history  |
|   git branches  |   GitBranches  |   git_branches  |   git_branches  |  n/a |    git branches    |
|    git files    |    GitFiles    |    git_files    |    git_files    |  n/a |      git files     |
|    git status   |    GitStatus   |    git_status   |       n/a       |  n/a | git modified files |
|    help grep    |    GrepHelp    |       n/a       |       n/a       |  n/a |   grep help docs   |
|    help tags    |       n/a      |    help_tags    |    help_tags    |  n/a |      help tags     |
|      jumps      |      Jumps     |       n/a       |     jumplist    |  n/a |      jump list     |
|      marks      |      Marks     |      marks      |      marks      |  n/a |      vim marks     |


fzfpreview
- BlamePR
- Ctags
- DirectoryFiles
- FromResources
- GitActions
- GitBranchActions
- GitCurrentLogs
- GitLogActions
- GitLogs
- GitReflogActions
- GitReflogs
- GitStashActions
- GitStashes
- GitStastusActions
- Lines
- LocationList
- MemoListGrep
- MemoList
- OldFiles
- ProjectFiles
- ProjectGrepRecallRpc
- QuickFix
- TodoComments
- VistaBufferCtags
- VistaCtags
- Yankround
- VistaBufferCtags

fzflua
- btags
- colorschemes
- files
- files_resume
- filetypes
- fzf_files
- git_bcommits
- git_commits
- grep
- grep_cWORD
- grep_curbuf
- grep_cword
- grep_last
- grep_visual
- keymaps
- lines
- live_grep
- live_grep_native
- live_grep_resume
- loclist
- lsp_code_actions
- lsp_declarations
- lsp_definitions
- lsp_document_diagnostics
- lsp_document_symbols
- lsp_implementations
- lsp_live_workspace_symbols
- lsp_references
- lsp_typedefs
- lsp_workspace_diagnostics
- lsp_workspace_symbols
- man_pages
- marks
- oldfiles
- packadd
- quickfix
- registers
- setup
- spell_suggest
- tabs
- tags

Telescope
- arecibo
- autocommands
- colorscheme
- current_uffer_tags
- fd
- file_browser
- filetypes
- find_files
- git_bcommits
- git_commits
- git_stash
- grep_string
- highlights
- keymaps
- live_grep
- loclist
- lsp_code_actions
- lsp_definitions
- lsp_document_diagnostics
- lsp_document_symbols
- lsp_dynamic_workspace_symbols
- lsp_implementations
- lsp_range_code_actions
- lsp_references
- lsp_type_definitions
- lsp_workspace_diagnostics
- lsp_workspace_symbols
- man_pages
- mapper
- marks
- oldfile
- planets
- quickfix
- registers
- reloader
- resume
- search_history
- spell_suggest
- symbols
- tags
- tagstack
- treesitter
- vim_options
- YankHistoryPaste

environment
:abbreviate   - list abbreviations
:args         - argument list
:augroup      - augroups
:autocmd      - list auto-commands
:breaklist    - list current breakpoints
:cabbrev      - list command mode abbreviations
:cmap         - list command mode maps
:compiler     - list compiler scripts
:digraphs     - digraphs
:file         - print filename, cursor position and status (like Ctrl-G)
:filetype     - on/off settings for filetype detect/plugins/indent
:function     - list user-defined functions (names and argument lists but not the full code)
:function Foo - user-defined function Foo() (full code list)
:highlight    - highlight groups
:history =    - expression history
:history s    - search history
:history      - your commands
:iabbrev      - list insert mode abbreviations
:imap         - list insert mode maps
:intro        - the Vim splash screen, with summary version info
:jumps        - your movements
:language     - current language settings
:let          - all variables
:let FooBar   - variable FooBar
:let g:       - global variables
:let v:       - Vim variables
:list         - buffer lines (many similar commands)
:lmap         - language mappings (set by keymap or by lmap)
:ls           - buffers
:ls!          - buffers, including "unlisted" buffers
:map!         - Insert and Command-line mode maps (imap, cmap)
:map          - Normal and Visual mode maps (nmap, vmap, xmap, smap, omap)
:map<buffer>  - buffer local Normal and Visual mode maps
:map!<buffer> - buffer local Insert and Command-line mode maps
:marks        - marks
:menu         - menu items
:messages     - message history
:nmap         - Normal-mode mappings only
:omap         - Operator-pending mode mappings only
:print        - display buffer lines (useful after :g or with a range)
:reg          - registers
:scriptnames  - all scripts sourced so far
:set all      - all options, including defaults
:setglobal    - global option values
:setlocal     - local option values
:set          - options with non-default value
:set termcap  - list terminal codes and terminal keys
:smap         - Select-mode mappings only
:spellinfo    - spellfiles used
:syntax       - syntax items
:syn sync     - current syntax sync mode
:tabs         - tab pages
:tags         - tag stack contents
:undolist     - leaves of the undo tree
:verbose      - show info about where a map or autocmd or function is defined
:version      - list version and build options
:vmap         - Visual and Select mode mappings only
:winpos       - Vim window position (gui)
:xmap         - visual mode maps only
