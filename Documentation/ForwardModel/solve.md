---
layout: docs
title: ForwardModel.solve Function Documentation
permalink: /Documentation/ForwardModel/solve
---

# solve
Solves the forward model

## Syntax
<a href="#d1"><code class="hang">T0tilde = <wbr>solve(<wbr>fm,<wbr>film_args,<wbr>sub_args,<wbr>Rth,<wbr>ex_args,<wbr>f0)</code></a><br>
<a href="#d2"><code class="hang">T0tilde = <wbr>solve(<wbr>fm,<wbr>film_args,<wbr>sub_args,<wbr>Rth,<wbr>ex_args,<wbr>f0,<wbr>X_probe)</code></a><br>

## Description
<a id="d1"></a>
<code><a href="#T0tilde-out">T0tilde</a> = <wbr>solve(<wbr><a href="#fm-in">fm</a>,<wbr><a href="#film_args-in">film_args</a>,<wbr><a href="#sub_args-in">sub_args</a>,<wbr><a href="#Rth-in">Rth</a>,<wbr><a href="#ex_args-in">ex_args</a>,<wbr><a href="#f0-in">f0</a>)</code> solves the forward model given material and experimental parameters, evaluated at <code>X_probe(i,j) = [fm.solver.x(i), fm.solver.y(j)]</code>.
<hr>
<a id="d2"></a>
<code><a href="#T0tilde-out">T0tilde</a> = <wbr>solve(<wbr><a href="#fm-in">fm</a>,<wbr><a href="#film_args-in">film_args</a>,<wbr><a href="#sub_args-in">sub_args</a>,<wbr><a href="#Rth-in">Rth</a>,<wbr><a href="#ex_args-in">ex_args</a>,<wbr><a href="#f0-in">f0</a>,<wbr><a href="#X_probe-in">X_probe</a>)</code> solves the forward model given material and experimental parameters, evaluated at the input probe location(s) <code><a href="#X_probe-in">X_probe</a></code>.

## Input Arguments
<details class="custom-details" id="fm-in">
    <summary>
        <span class="summary-text">
            <b><code>fm</code> - Input <code>ForwardModel</code> object</b>
            <span class="subline">
              <a href="{{ '/Documentation/ForwardModel' | relative_url }}"><code>ForwardModel</code></a> object
            </span>
        </span>
    </summary>
    <div>
        <p>
            The input <code>ForwardModel</code> object specifies essential solver parameters. See <a href="{{ '/Documentation/ForwardModel' | relative_url }}"><code>ForwardModel</code> Documentation</a> for more details.
        </p>
        <p>
            <b>Data Type:</b> <a href="{{ '/Documentation/ForwardModel' | relative_url }}"><code>ForwardModel</code></a>
        </p>
    </div>
</details>

<details class="custom-details" id="film_args-in">
    <summary>
        <span class="summary-text">
            <b><code>film_args</code> - Material arguments for the film layer</b>
            <span class="subline">
              cell vector
            </span>
        </span>
    </summary>
    <div>
        <p>
            ...
        </p>
        <p>
            <b>Data Type:</b> cell
        </p>
    </div>
</details>

## Output Arguments

## See Also




