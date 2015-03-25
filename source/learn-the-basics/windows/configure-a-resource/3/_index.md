## 3. Create the INI file

First, you need to create the INI file and set its initial contents. To keep things basic, let's configure the file in the working directory.

From your `~\chef-repo` directory, create a file named <code class="file-path">hello.rb</code>, add these contents, and then save the file.

```ruby-Win32
# ~\chef-repo\hello.rb
file 'C:\Users\Administrator\chef-repo\settings.ini' do
  content 'greeting=hello world'
end
```

From the command prompt, run the following `chef-apply` command to apply what you've written.

```ps
# ~\chef-repo
$ chef-apply hello.rb
Recipe: (chef-apply cookbook)::(chef-apply recipe)
  * file[C:\Users\Administrator\chef-repo\settings.ini] action create
    - create new file C:\Users\Administrator\chef-repo\settings.ini
    - update content in file C:\Users\Administrator\chef-repo\settings.ini from none to 6823fa
    --- C:\Users\Administrator\chef-repo\settings.ini    2014-08-16 01:04:33.000000000 +0000
    +++ C:/Users/ADMINI~1/AppData/Local/Temp/2/settings.ini20140816-2080-5hrzgl     2014-08-16 01:04:33.000000000 +0000
    @@ -1 +1,2 @@
    +greeting=hello world
```

The output tells us that a new file, <code class="file-path">settings.ini</code>, was created.

Run the `Get-Content` PowerShell cmdlet to verify that the file was written.

```ps
# ~\chef-repo
$ Get-Content settings.ini
greeting=hello world
```

### Run the command a second time

Now, let's see now what happens when you run the same command again.

```ps
# ~\chef-repo
$ chef-apply hello.rb
Recipe: (chef-apply cookbook)::(chef-apply recipe)
  * file[C:\Users\Administrator\chef-repo\settings.ini] action create (up to date)
```

This time you get a different response &ndash; the file is already up to date. This is because Chef does work only when it needs to.

Chef looks at the current configuration state and applies the action only if the current state doesn't match the desired state. Here, Chef doesn't create or modify <code class="file-path">settings.ini</code> because it already exists and its contents didn't change.