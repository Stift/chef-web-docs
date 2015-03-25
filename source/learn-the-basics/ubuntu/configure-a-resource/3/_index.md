## 3. Update the MOTD file's contents

Now you're going to change the MOTD.

Modify <code class="file-path">hello.rb</code> like this ('hello world' becomes 'hello chef'.)

```ruby
# ~/chef-repo/hello.rb
file 'motd' do
  content 'hello chef'
end
```

Run `chef-apply`.

```bash
# ~/chef-repo
$ chef-apply hello.rb
Recipe: (chef-apply cookbook)::(chef-apply recipe)
  * file[motd] action create
    - update content in file motd from de031d to b1522f
    --- motd        2014-05-13 14:52:54.025253948 -0700
    +++ /tmp/.motd20140513-4015-13xpiup  2014-05-13 15:00:07.284522132 -0700
    @@ -1,2 +1,2 @@
    -hello world
    +hello chef
```

This time Chef does work because we've changed the desired state of the file and need to update the installed version to match it.