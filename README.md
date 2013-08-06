# paredit-widget

Paredit-widget provides paredit-style structural editing of clojure code, a la carte. It simply hooks up paredit.clj to a JTextArea, and provides the necessary keymappings.

Tested on on OS X (so far). Bug reports and pull requests welcome. 

## Rationale

The main bottleneck for innovation in clojure programming tools is the support for paredit. Paredit is a mandatory feature.

From a reuse standpoint, there is no need for every tool to reimplement paredit.

From a conceptual standpoint, its an error to intertwine code editing with concerns such as file management, debugging, etc, as is typically done in IDEs.

Every programming tool carries with it a set of assumptions of what programming, or a program, is. 

The goal of paredit-widget is to provide a simple, reusable implemention of the necessities of clojure editing, so that alternative programming environments can be explored.

Because the JVM is the premier clojure platform, paredit-widget is targeted for the JVM and uses Swing. Contributions for a clojurescript port are welcome.

## Usage

Paredit-widget supports most standard paredit commands, with their natural bindings. Check the paredit-widget.core/keymap var for the keymap. 

clone the repo, or add to your project dependencies:

    [org.kovas/paredit-widget "0.1.0-SNAPSHOT"]

(at this stage it's recommended to work from source)

require the namespace:

    (require '[paredit-widget.core :as p])

create a swing-based widget:

    (p/paredit-widget "(foo bar)") 

once created, it can be displayed and further manipulated using the standard swing apis (or with seesaw).

create and display an example widget:

    (p/test-paredit-widget)
  
## Implementation notes

Paredit-widget supports most of the commonly-used paredit commands. It uses paredit.clj to perform the underlying manipulations.

It has been tested on OS X.

Most of the complexity in the implementation has to do with properly supporting the alt/option key on the Mac. The workaround strategy may not work on international keyboards, but can be made pluggable.






## License

Copyright © 2013 Kovas Boguta

Distributed under the Eclipse Public License, the same as Clojure.
