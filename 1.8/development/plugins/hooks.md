---
layout: page
title:  "Plugin Hooks"
categories: [plugins]
---

# MyBB Hooks

The following hooks are available to plugins in MyBB version code <strong>{{ site.data.18_plugin_hooks.version_code }}</strong>.

<table class="standard_table">
    <thead>
        <tr>
            <th class="tcat">Name</th>
            <th class="tcat">File</th>
            <th class="tcat">Line</th>
        </tr>
    </thead>
    <tbody>
        {% assign hooks = site.data.18_plugin_hooks.hooks | sort: 'file' %}
        {% for hook in hooks %}
        <tr>
            <td>
                <code>{{ hook.name }}</code>
                {% if hook.parameters %}
                    <br>
                    <small><strong>Parameters:</strong> {{ hook.parameters | join: ', ' }}</small>
                {% endif %}
            </td>
            <td>{{ hook.file }}</td>
            <td><a href="https://github.com/mybb/mybb/blob/mybb_{{ site.data.18_plugin_hooks.version_code }}/{{ hook.file }}#L{{ hook.line }}">{{ hook.line }}</a></td>
        </tr>
        {% endfor %}
    </tbody>
</table>
