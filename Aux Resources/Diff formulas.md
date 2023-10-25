# Derivative Definition
$$
f'(x) = \lim_{h \to 0} \frac{f(x+h) - f(x)}{h}
$$

# Basic Properties
$$
\frac{d}{dx}cf(x) = cf'(x)
$$

$$
\frac{d}{dx}[f(x) + g(x)] = f'(x) + g'(x)
$$

# Chain Rule
$$
\frac{dy}{dx} = \frac{dy}{du} \frac{du}{dx}
$$

# Mean Value Theorem 
If $f(x)$ is continuous on $[a,b]$ and differentiable on $(a,b)$, then there exists a point $c$ in $(a,b)$ such that:
$$
f'(c) = \frac{f(b)-f(a)}{b-a}
$$

# Product Rule
$$
\frac{d}{dx}[f(x)g(x)] = f'(x)g(x) + f(x)g'(x) 
$$

# Quotient Rule
$$
\frac{d}{dx}\left[\frac{f(x)}{g(x)}\right] = \frac{f'(x)g(x) - f(x)g'(x)}{[g(x)]^2}
$$

# Power Rule
$$
\frac{d}{dx}[x^n] = nx^{n-1}
$$

# Properties of Limits
$$
\lim_{x\to c} [f(x) + g(x)] = \lim_{x\to c} f(x) + \lim_{x\to c} g(x) 
$$

$$
\lim_{x\to c} [f(x)g(x)] = \left(\lim_{x\to c} f(x)\right)\left(\lim_{x\to c} g(x)\right)
$$

# L'Hopital's Rule
If $\lim_{x\to c} f(x) = \lim_{x\to c} g(x) = 0$ or $\infty$, and $f$ and $g$ are diffentiable:  
$$
\lim_{x\to c} \frac{f(x)}{g(x)} = \lim_{x\to c} \frac{f'(x)}{g'(x)}
$$

# Common Derivatives
## Trignometric
$$
\frac{d}{dx} \sin(x) = \cos(x)
$$

$$
\frac{d}{dx} \cos(x) = -\sin(x)
$$

$$
\frac{d}{dx} \tan(x) = \sec^2(x)
$$ 

$$
\frac{d}{dx} \cot(x) = -\csc^2(x)
$$

$$
\frac{d}{dx} \sec(x) = \sec(x)\tan(x)  
$$

$$
\frac{d}{dx} \csc(x) = -\csc(x)\cot(x)
$$
$$
\frac{d}{dx} \sin^{-1}(x) = \frac{1}{\sqrt{1-x^2}} 
$$

$$
\frac{d}{dx} \cos^{-1}(x) = -\frac{1}{\sqrt{1-x^2}}
$$

$$ 
\frac{d}{dx} \tan^{-1}(x) = \frac{1}{1+x^2} 
$$
## Exponent and Logs
$$
\frac{d}{dx} e^x = e^x
$$

$$
\frac{d}{dx} \ln(x) = \frac{1}{x}
$$

$$
\frac{d}{dx} a^x = a^x\ln(a)  
$$ 

$$
\frac{d}{dx} \log_a(x) = \frac{1}{x\ln(a)}
$$

$$
\frac{d}{dx} \sqrt{x} = \frac{1}{2\sqrt{x}}
$$

$$
\frac{d}{dx} x^n = nx^{n-1}
$$



[[Integ Formulas]]