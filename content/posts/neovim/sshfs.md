---
title: "(Neo)vim - Editing Remote Files with SSHFS"
date: 2020-05-04T17:56:17-04:00
draft: false
---

# Prefer Video?

**[Video form of this blog post](https://www.youtube.com/watch?v=0fAygjWHpdM)**

### tl;dr

1. Install [SSHFS](https://github.com/libfuse/sshfs) via your package manager
2. Create a mount dir (e.g. `~/mysite.com`)
3. `sshfs -o default_permissions myusername@mysite.com:/ ~/mysite.com`

## Functionality

Using SSHFS, we can mount a remote directory to our local file system and edit files with ease.

- Use our local (neo)vim settings and plugins
- Explore the remote file system (just like using ssh)
- Files are updated on the server on file save

The biggest advantage for me is being able to use my local (neo)vim setup. I used to install my particular setup on each server I administer, but that's unnecessary when using SSHFS.

## Setup

1. Install SSHFS via your package manager (e.g. `pacman -S sshfs`, `apt install sshfs`)
2. Create a directory where you will mount the remote file system: 

```sh

$ mkdir ~/mysite.com

```

3. Mount your server's filesystem to the above mount point you've created:

```sh

$ sshfs -o default_permissions myusername@mysite.com:/ ~/mysite.com

```

### Explaining the above command

- `-o` is the option flag (see `man sshfs`).
    - `default_permissions` - By default, any user able to access our mount point `~/mysite.com` will be able to edit remote files. Enabling this option will use the permissions set up on the remote file system.

- `myusername@mysite.com` - The remote user's name and the remote URL or IP address.
- `:` - A delimiter (separator) between the URL and the file system location to mount.
- `/` - The mount point on the remote file system (the root directory in this case). This can be changed, e.g. `/home/myusername` to mount your remote home directory.
- `~/mysite.com` - The mount point on the local filesystem that you created earlier in this guide.

## Unmounting

Typically unmounting can be done with the `umount` command, but sometimes the file system will hang saying the resource is busy.

In this case, we are able to unmount the file system with `fusermount -zu ~/mysite.com`

## Advantages of SSHFS over scp

When using `scp` (which Neovim has issues with*), we are not able to freely explore the remote file system and use file searching tools (such as [fzf](https://blog.avahe.tk/posts/neovim/fzf-ripgrep/)).

Having the remote file system mounted locally makes for a very fluid workflow, and you don't have to remember exactly file names or locations.

***Neovim seems to have issues with scp, where the user will not be prompted for their remote password (when using password auth instead of ssh keys).**

