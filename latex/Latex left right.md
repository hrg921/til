# Latex left right

\left and \right are used for delimiters when they have to change the size dynamically depending on the content

```latex
\left
\right
```

```latex
\documentclass{article}
\usepackage{amsmath}


\begin{document}
Compare this:
 \begin{align*}
 \left(\sqrt{2}+\sqrt{3}\right)^2
            &=\left(\sqrt{2}\right)^2+2\times\sqrt{2}\times\sqrt{
                3}+\left(\sqrt{3}\right)^2\\
            &=2+2\sqrt{6}+3\\
            &=5+2\sqrt{6}
\end{align*}
with:
\begin{align*}
 (\sqrt{2}+\sqrt{3})^2
            &=(\sqrt{2})^2+2\times\sqrt{2}\times\sqrt{
                3}+(\sqrt{3})^2\\
            &=2+2\sqrt{6}+3\\
            &=5+2\sqrt{6}
\end{align*}
First one uses \verb|\left(| and \verb|\right)| and second one uses just \verb|(| and \verb|)|. I hope the difference is clear. 

Just another example:    
\[\left(\frac{1}{2}\right) \qquad (\frac{1}{2})\]

\end{document} 
```