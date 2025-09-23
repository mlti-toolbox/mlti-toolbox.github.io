---
layout: docs
title: IFTSolver Class Documentation
permalink: /Documentation/IFTSolver
---

# IFTSolver

## Description

## Creation

### Syntax
<a href="#d1"><code class="hang">solver = IFTSolver(<wbr>method)</code></a><br>
<a href="#d2"><code class="hang">solver = IFTSolver(<wbr>"ifft2",<wbr>Name,<wbr>Value)</code></a>

### Description
<a id="d1"></a>
`solver = IFTSolver(`<wbr>`method)` creates an `IFTSolver` object that uses the specified method to solve the 2D inverse Fourier transform.
<p>
  \(
    \tilde{T}_0 \left( x, y, f \right) = 
    \int_{-\infty}^\infty \int_{-\infty}^\infty 
    \hat{T}_0 \left( u, v, f \right) \, 
    \exp \left( 2 i \pi \left( u x + v y \right) \right) \, du \, dv
  \)
</p>
<p>
  This syntax is only valid for <code>method ∈ {integral2, vpaintegral}</code>.  When <code>method = ifft2</code>, name-value arguments are required.
</p>
<hr>
<a id="d2"></a>
`solver = IFTSolver(`<wbr>`"ifft2",`<wbr>[`Name,Value`](#name-value-arguments)`)` creates an `IFTSolver` object that uses MATLAB's built-in [`ifft2`](https://www.mathworks.com/help/matlab/ref/ifft2.html) method—with options specified as name-value arguments—to solve the 2D inverse Fourier transform.

### Input Arguments

<details class="custom-details" id="method-argument">
    <summary>
        <span class="summary-text">
            <b><code>method</code> - 2D inverse Fourier transform method</b>
            <span class="subline">
              <code>"ifft2"</code> | <code>"integral2"</code> | <code>"vpaintegral"</code> | <a href="{{ '/Documentation/IFTEnum' | relative_url }}"><code>IFTEnum</code></a> object
            </span>
        </span>
    </summary>
    <div>
        <p>
            2D inverse Fourier transform method. When possible, the
            <a href="https://www.mathworks.com/help/matlab/ref/ifft2.html"><code>ifft2</code></a>
            method should be used for its computational efficiency.
            However, if greater accuracy is needed, the
            <a href="https://www.mathworks.com/help/matlab/ref/integral2.html"><code>integral2</code></a> or <a href="https://www.mathworks.com/help/releases/R2025a/symbolic/sym.vpaintegral.html"><code>vpaintegral</code></a>
            method may be used instead.
        </p>
        <p>
            When <code>method = "ifft2"</code>, name-value arguments must also be provided.
        </p>
        <p>
            <code>char</code> and <code>string</code> inputs are <i>case-insensitive</i> and may be specified as a unique leading substring of any one of the above listed options.
        </p>
        <p>
            <b>Data Types:</b> <code>char</code> | <code>string</code> | <a href="{{ '/Documentation/IFTEnum' | relative_url }}"><code>IFTEnum</code></a>
        </p>
    </div>
</details>

### Name-Value Arguments

<details class="custom-details" id="x_max-argument">
    <summary>
        <span class="summary-text">
            <b><code>x_max</code> - Maximum spatial distance from pump</b>
            <span class="subline">
              positive real scalar | 1-by-2 positive real vector
            </span>
        </span>
    </summary>
    <div>
        <p>
            Maximum spatial distance from the pump in the x- and y-directions used in the 2D inverse fast Fourier transform
            (<a href="https://www.mathworks.com/help/matlab/ref/ifft2.html"><code>ifft2</code></a>).
        </p>
      <p>
        When provided as a scalar, <code>dx</code> is expanded (copied) to a 1-by-2 vector.
      </p>
        <p>
            <b>Data Types:</b> <code>double</code> | <code>single</code>
        </p>
    </div>
</details>

<details class="custom-details" id="dx-argument">
    <summary>
        <span class="summary-text">
            <b><code>dx</code> - Discrete spatial step size</b>
            <span class="subline">
              positive real scalar | 1-by-2 positive real vector
            </span>
        </span>
    </summary>
    <div>
        <p>
            Discrete spatial step size—i.e., sampling period—in the x- and y-directions used in the 2D inverse fast Fourier transform
            (<a href="https://www.mathworks.com/help/matlab/ref/ifft2.html"><code>ifft2</code></a>).
        </p>
      <p>
        When provided as a scalar, <code>dx</code> is expanded (copied) to a 1-by-2 vector.
      </p>
        <p>
          When not provided or when set equal to 0, <code>dx</code> is calculated as <code>x_max / floor(Nx/2)</code>.
        </p>
        <p>
            <b>Data Types:</b> <code>double</code> | <code>single</code>
        </p>
    </div>
</details>

<details class="custom-details" id="Nx-argument">
    <summary>
        <span class="summary-text">
            <b><code>Nx</code> - Number of spatial steps</b>
            <span class="subline">
              [256, 256] (default) | positive integer scalar | 1-by-2 positive integer vector
            </span>
        </span>
    </summary>
    <div>
        <p>
            Number of discrete spatial points—i.e., signal length—in the x- and y-directions used in the 2D inverse fast Fourier transform
            (<a href="https://www.mathworks.com/help/matlab/ref/ifft2.html"><code>ifft2</code></a>).
        </p>
        <p>
            When possible, the value of <code>Nx</code> should have only small prime factors as this results in significantly faster execution of the
            <a href="https://www.mathworks.com/help/matlab/ref/ifft2.html"><code>ifft2</code></a> transform.
        </p>
      <p>
        When provided as a scalar, <code>Nx</code> is expanded (copied) to a 1-by-2 vector.
      </p>
      <p>
        When not provided or when set equal to 0, if both <code>x_max</code> and <code>dx</code> are provided <code>Nx</code> is calculated as <code>floor(x_max/dx) * 2 + 1</code>; otherwise, the default value will be used.
      </p>
        <p>
            <b>Data Types:</b> <code>double</code> | <code>single</code> | <code>int8</code> | <code>int16</code> | <code>int32</code> | <code>uint8</code> | <code>uint16</code> | <code>uint32</code>
        </p>
    </div>
</details>

<details class="custom-details" id="interp_method-argument">
    <summary>
        <span class="summary-text">
            <b><code>interp_methods</code> - Interpolation and extrapolation methods</b>
            <span class="subline">
              <code>["linear","linear"]</code> (default) | [Method, ExtrapolationMethod]
            </span>
        </span>
    </summary>
    <div>
        <p>
            Interpolation and extrapolation methods for the creation of the <a href="#interp-property"><code>interp</code></a> property. See <a href="https://www.mathworks.com/help/releases/R2025a/matlab/ref/griddedinterpolant.html"><code>griddedInterpolant</code></a> input arguments <a href="https://www.mathworks.com/help/releases/R2025a/matlab/ref/griddedinterpolant.html#bvh2cy0-Method"><code>Method</code></a> and <a href="https://www.mathworks.com/help/releases/R2025a/matlab/ref/griddedinterpolant.html#bvh2cy0-ExtrapolationMethod"><code>ExtrapolationMethod</code></a> for a list of available options.
        </p>
      <p>
        If provided as a scalar string or character vector, the input is used for both <code>Method</code> and <code>ExtrapolationMethod</code> (i.e., <code>ExtrapolationMethod = Method</code>)
      </p>
      <p>
        The interpolant will be created using the following command:<br>
      </p>
      <p>
      <code class="hang"><a href="#interp-property">interp</a> = <a href="https://www.mathworks.com/help/releases/R2025a/matlab/ref/griddedinterpolant.html">griddedInterpolant</a>(<wbr>{<a href="#x-property">x</a>,<a href="#y-property">y</a>},<wbr>zeros(<a href="#Nx-argument">Nx</a>(1),<a href="#Nx-argument">Nx</a>(2)),<wbr>interp_method(1),<wbr>interp_method(2))</code>
    </p>
        <p>
            <b>Data Types:</b> character array | cell of character arrays | string array
        </p>
    </div>
</details>

## Properties
In addition to storing the [`method`](#method-argument) argument as a property, the following properties are commputed and stored if the [`ifft2`](https://www.mathworks.com/help/matlab/ref/ifft2.html) method is used.

<details class="custom-details" id="x-property">
    <summary>
        <span class="summary-text">
            <b><code>x</code> - Discrete spatial vector</b>
            <span class="subline">
                Read only: double column vector
            </span>
        </span>
    </summary>
    <div>
      <p>
        Discrete spatial vector in the x-direction, calculated as <code>dx(1) * (-floor(Nx(1)/2) : ceil(Nx(1)/2) - 1)</code>.
      </p>
      <p>
        <b>Data Type:</b> <code>double</code>
      </p>
    </div>
</details>

<details class="custom-details" id="y-property">
    <summary>
        <span class="summary-text">
            <b><code>y</code> - Discrete spatial vector</b>
            <span class="subline">
                Read only: double row vector
            </span>
        </span>
    </summary>
    <div>
      <p>
        Discrete spatial vector in the y-direction, calculated as <code>dx(2) * (-floor(Nx(2)/2) : ceil(Nx(2)/2) - 1)</code>.
      </p>
      <p>
        <b>Data Type:</b> <code>double</code>
      </p>
    </div>
</details>

<details class="custom-details" id="u-property">
    <summary>
        <span class="summary-text">
            <b><code>u</code> - Discrete spatial-frequency vector</b>
            <span class="subline">
                Read only: double column vector
            </span>
        </span>
    </summary>
    <div>
      <p>
        Discrete spatial-frequency vector in the x-direction, calculated as <code>(-floor(Nx(1)/2) : ceil(Nx(1)/2) - 1) / (Nx(1) * dx(1))</code>.
      </p>
      <p>
        <b>Data Type:</b> <code>double</code>
      </p>
    </div>
</details>

<details class="custom-details" id="v-property">
    <summary>
        <span class="summary-text">
            <b><code>v</code> - Discrete spatial-frequency vector</b>
            <span class="subline">
                Read only: double row vector
            </span>
        </span>
    </summary>
    <div>
      <p>
        Discrete spatial-frequency vector in the y-direction, calculated as <code>(-floor(Nx(2)/2) : ceil(Nx(2)/2) - 1) / (Nx(2) * dx(2))</code>.
      </p>
      <p>
        <b>Data Type:</b> <code>double</code>
      </p>
    </div>
</details>

<details class="custom-details" id="interp-property">
    <summary>
        <span class="summary-text">
            <b><code>interp</code> - Interpolant</b>
            <span class="subline">
                Read only: scalar <a href="https://www.mathworks.com/help/releases/R2025a/matlab/ref/griddedinterpolant.html"><code>griddedInterpolant</code></a> object
            </span>
        </span>
    </summary>
    <div>
      <p>
        Interpolates the surface temperature data <code>T0tilde</code> defined on the discrete <code>(<a href="#x-property">x</a>, <a href="y-property">y</a>)</code> grid to estimate values at probe locations <code>X_probe</code>.
      </p>
      <p>
        <b>Usage:</b><br>
        <code class="hang">interp.Values = T0tilde;</code><br>
        <code class="hang">T0tilde = interp(X_probe);</code><br>
        Where <code>X_probe</code> is an <code>N_probe</code>-by-2 numeric matrix.
      </p>
      <p>
        <b>Data Type:</b> <a href="https://www.mathworks.com/help/releases/R2025a/matlab/ref/griddedinterpolant.html"><code>griddedInterpolant</code></a>
      </p>
    </div>
</details>

## Object Functions
<table>
  <tr>
    <td>
      <a href="{{ '/Documentation/IFTSolver/solve' | relative_url }}"><code>solve</code></a>
    </td>
    <td>
      Solves the 2D inverse Fourier transform
    </td>
  </tr>
</table>
## Examples

## See Also
### MLTI Companion Classes and Methods
<a href="{{ '/Documentation/IFTEnum' | relative_url }}"><code>IFTEnum</code></a> | <a href="{{ '/Documentation/ForwardModel' | relative_url }}"><code>ForwardModel</code></a>

### MATLAB Methods
<a href="https://www.mathworks.com/help/matlab/ref/ifft2.html"><code>ifft2</code></a> | <a href="https://www.mathworks.com/help/matlab/ref/integral2.html"><code>integral2</code></a> | <a href="https://www.mathworks.com/help/releases/R2025a/symbolic/sym.vpaintegral.html"><code>vpaintegral</code></a> | <a href="https://www.mathworks.com/help/releases/R2025a/matlab/ref/griddedinterpolant.html"><code>griddedInterpolant</code></a>


