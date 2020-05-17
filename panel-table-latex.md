---
layout: none
comment: this is pretty close to raw latex
---
{% assign archive_base = "https://ideas-productivity.org/events/strategies-for-working-remotely-panels//\#panel" %}
<pre>
\begin{table}
\begin{tabular}{lp{0.85\textwidth}}
  \hline
  \textbf{Date} & \textbf{\emph{Title}, Panelist(s)} \\
  \hline
{% for panel in site.events %}
  {% capture seqnum %}{{ panel.panel-id | prepend: "00" | slice: -3, 3 }}{% endcapture %}
  {{ panel.date | date: "%F" }} & 
    {% raw %}\emph{\href{{% endraw %}{{ archive_base }}{{ seqnum }}{% raw %}}{{% endraw %}{{ panel.title}}{% raw %}}}{% endraw %}, {{ panel.author }} \\
  {% endfor %}
  \hline
\end{tabular}
\end{table}
</pre>
