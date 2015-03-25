## 3. Bootstrap your node

<div class="indent" id="bootstrap-intro" data-type="rhel-fundamentals" ng-non-bindable>
From your workstation, run this command to bootstrap your node. Replace <code>{{address}}</code> with your remote node's external address, <code>{{user}}</code> with your username, and <code>{{password}}</code> with your password.
</div>
<p/>
<div id="bootstrap-command" class="window" ng-non-bindable>
  <nav class="control-window">
    <div class="close">&times;</div>
    <div class="minimize"></div>
    <div class="deactivate"></div>
  </nav>
  <h1 class="titleInside">Terminal: ~/chef-repo</h1>
  <div class="container" data-type="rhel-fundamentals"><div class="terminal"><table>
    <tbody>
      <tr>
        <td class="gutter"><pre class="line-numbers"><span class="line-number">$</span></pre></td>
        <td class="code"><pre><code><span class="line command">knife bootstrap {{address}} --ssh-user {{user}} --ssh-password '{{password}}' --sudo --use-sudo-password --node-name node1 --run-list 'recipe[learn\_chef\_httpd]'</span></code></pre></td>
      </tr>
    </tbody></table></div></div>
</div>

[COMMENT] This is a long command &ndash; use the scrollbar to see the entire thing.

The optional `--node-name` argument uniquely identifies the node with the Chef server. Its value can be whatever you want. The server's FQDN is the default. If you previously used the name `node1` to bootstrap a different node, you'll need to choose a different name or remove the previous node.