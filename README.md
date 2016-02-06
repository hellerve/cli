# cli

cli is a simple library for creating composable command
line interfaces in zepto.

## Usage

```clojure
(import-all "cli")

; The argument structure looks like this (similarish to argparse):
(define install-args
  #{"pleasedo"
    #{:type     :number
      :default  10
      :required #f
      :usage    foo you}})

; This adds commands to the toplevel CLI.
(cli:create (list
              (cli:command "install"  install  install-args)
              (cli:command "register" register register-args)
              (cli:command "upgrade"  upgrade  upgrade-args)))
; this adds commands to the install endpoint
(cli:create (cli:command "help" help-install []) "install")

(cli:play)
```

<hr/>

Have fun!
