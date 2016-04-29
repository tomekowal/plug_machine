# PlugMachine

**REST helpers based around plug. https://github.com/elixir-lang/plug 
inspired by webmachine https://github.com/basho/webmachine**

Webmachine from Basho allows creation of endpoints that comply with REST
by implementing callback functions.
Values returned by those function determine request path in decision graph
https://raw.githubusercontent.com/wiki/basho/webmachine/images/http-headers-status-v3.png

Webmachine also enables easy debugging by tracing the request path
in decision tree and visualising it interactively.

Webmachine can't be easily integrated inside Phoenix applicaations,
because it has its own request dispatch mechanism and isn't based on Plug.
There are however many similarities.
All callbacks (resource functions) have signature:

    f(ReqData, Context) -> {Result, ReqData, Context}

The `ReqData` and `Result` can be mapped to fields inside `Plug.Conn`
while `Context` can be passed in `Conn.Assigns`.

This means that those functions can be easily translated to plugs.

The main goal of this project is to have easy to implement and debug 
REST controllers inside Phoenix.

There is a similar project https://github.com/awetzel/ewebmachine
I hope to achieve similar results without using as many macros.

## Installation

If [available in Hex](https://hex.pm/docs/publish), the package can be installed as:

  1. Add plug_machine to your list of dependencies in `mix.exs`:

        def deps do
          [{:plug_machine, "~> 0.0.1"}]
        end

  2. Ensure plug_machine is started before your application:

        def application do
          [applications: [:plug_machine]]
        end

