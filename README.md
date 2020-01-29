# cli

A simple CLI library for Carp.

```clojure
(load "https://veitheller.de/git/carpentry/cli@master")

(defn main []
  (let [p (=> (CLI.new @"My super cool tool!")
              (CLI.add &(CLI.int "flag" "f" "my flag" true))
              (CLI.add &(CLI.str "thing" "t" "my thing" false @"hi" &[@"a" @"b" @"hi"])))]
    (match (CLI.parse &p)
      (Result.Success flags)
        (println* &(str &(Map.get &flags "flag")) " " &(str &(Map.get &flags "thing")))
      (Result.Error msg) (do (IO.errorln &msg) (CLI.usage &p)))))
```

## Installation

```clojure
(load "https://veitheller.de/git/carpentry/cli@master")
```

## Usage

<hr/>

Have fun!
