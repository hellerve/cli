# cli

cli is a simple library for creating composable command
line interfaces in zepto.

## Usage

```clojure
(import-all "cli")

; The argument structure looks like this (similarish to argparse):
(define add-args
  #{:help      "adds 1 to a number"
    :options #{"pleasedo" #{:type     :number
                            :default  "10"
                            :required #t
                            :usage    "foo you"}}})

; This adds commands to the toplevel CLI.
(define x (cli:create (list (cli:command "add" (lambda (x) (add1 (x "pleasedo"))) add-args))))
; this adds commands to the install endpoint
(define y (cli:create (cli:command "write-foo" (lambda (x) (write "foo")) #{}) "add" x))

; Get the party started.
; Optionally takes a script name (if it deviates from the file name)
; and a list of arguments (if you want to do your own processing before)
; of the form #{:args ("list" "of" "arguments") :name "my-cool-alternative-name"}
(cli:play y)
```

<hr/>

Have fun!
