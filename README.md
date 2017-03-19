# daisly - Intelisense for lua and moonscript

Started as a fork of [lua-inspect](https://github.com/davidm/lua-inspect)


# Features 

- analysis:
        * identifies global (red) and local variables (blue), including locals that are
	   function arguments (dark blue) and upvalues (light blue)
        * identifies unused local variables: e.g. `do local x=1 end` (white-on-blue)
        * identifies local variables masking other locals (same name): e.g. `local x=1; local x=2`
	   (strikethrough and squiggle line)
        * identifies local variables that have non-constant binding (`local x = 1; x = 2`) (italic)
        * identifies unknown global variables (white-on-red) and table fields (red), inferred by
	   static and dynamic evaluation.
        * infers values of variables (e.g. `local sum = math.pi + 2` is 5.14.
           and defined-ness of members of imported modules
          (`local mt = require "math"; math.sqrtt(2) -- undefined`)
        * infers signatures of functions (including local, global, and module functions)
        * checks number of function arguments against signatures
        * cross-references variables (locals and module fields) with their definitions and uses
	  (pink highlight), identifies range of lines/scope where the local is defined
	   and (SciTE only) supports jump-to-definition and jump-to-uses
        * identifies all keywords in selected block (underline)
        * evaluate special comments (prefixed by '!') to inject semantic information into analysis
           (similar to luaanalyze / lint).
        * basic type inferences (e.g. number + number -> number)
- infer function return values (e.g. `function f(x) if x then return 1,2,3 else return 1,3,'z' end end`
	   returns 1, number, unknown).
- detect dead-code (e.g. `do return end dead()`) (SciTE only) (diagonal hatching)
    * refactoring:
        * command to rename all occurrences of selected variable (SciTE only)
    * browsing:
        * inspect members of selected table.
        * select statement or comment containing current cursor selection (SciTE only)
        * display real-time annotations of all local variables, like an Excel/Mathcad worksheet
          (experimental feature via ANNOTATE_ALL_LOCALS) (currently SciTE only)
    * auto-complete typing support (SciTE only) (experimental)
    * interfaces: SciTE plugin, VIM plugin, and HTML output.

