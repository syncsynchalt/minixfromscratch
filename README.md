# MINIX from Scratch

## Why MINIX?

Until now, I have not been able to find a MINIX 3 project that allows you to compile the code that is referenced in the book *Operating Systems: Design and Implementation (3e)* (v3.1.0). It was tricky to get a reasonable development setup to make it possible for newbies like myself to learn from the book. This is an attempt to fix that and make it easy to browse, edit, recompile, and execute the code.

Why should you learn MINIX instead of Linux? Or rather than another teaching OS such as xv6, NachOS, or Xinu?

Unlike most of these systems, MINIX:
-Is heavily commented.
-Comes with three highly detailed books as its primary form of documentation.
-Has a much smaller and easier to understand kernel (it helps that it's a microkernel).
-Runs quite well on an emulator without melting your CPU (at least since the 2nd edition).

Although xv6 and these other systems have been valuable tools for me (and may have extra features, like threads and NAT), I have found that the MINIX documentation is the most extensive and detailed.

## Screenshots:

The login screen:

Using the built-in partition editor, `part`:

Navigating the code in /usr/src:

Recompiling the system:

## Minimal working example:
Assuming you have QEMU installed, run `./qemuminix3.sh`. After it boots, you can login with username "root" and no password. To edit the code and recompile:

- Exit MINIX with CTRL+ALT+DEL (if you do not, you may lose files that were not synced to the hard disk). You'll then need to close QEMU manually (MINIX doesn't know how).
- Mount the root, usr, and home partitions with `./mountminix3`. Linux requires superuser permissions to mount a file system.
- Make your edits to the code (for a start, maybe try modifying the [boot message](LINK GOES HERE) in usr/src/kernel/main.c).
- Unmount the filesystems using `./umountminix3.sh` (also requires sudo).
- Start the system again with `./qemuminix3.sh`

## Why learn MINIX instead of Linux:

Relevant quotes from Andy Tanenbaum:
-(quote about young linus in college)

-(another relevant quote from andy tanenbaum about how small microkernel OS are much easier to understand)


MINIX is a great tool for learning about Linux. MINIX is like a small and simplified version of Linux - Linus took heavy inspiration from it, and his legendary [("nothing big")](LINK GOES HERE) post announcing Linux was first posted on the comp.os.minix newsboard. Within MINIX you will find many familiar Linux tools and features, including:

- A similar directory structure: files such as /etc/utmp, /etc/passwd, /dev are where you expect them to be.
- A Bash interpreter (ash) with source code.
- Similar filesystem conventions: just as in Linux, you can mount filesystems directly onto the root filesystem with `mount`.
- A similar system administration structure, with familiar utilities like `chmod`, `mkfs`, `mkisofs` (`genisoimage`), `part` (similar to `fdisk` or `parted`) an Emacs clone (elle) and a Vim clone (evil). 

## MINIX is useful for learning about:

- Operating systems 
- Cybersecurity
- Networking 
- System administration
- Computer architecture
- Compilers (MINIX ships with it's own miniature C compiler, ACKPACK)
- Filesystems and disk partitioning
- Hardware
- Bash scripting
- Data structures and algorithms

## Making your own hard disk image:
To make a bootable and editable hard disk image, you'll need to install from the official MINIX CD. You can find it at [minix3.org](minix3.org). MINIX 3 comes with a `setup.sh` utility in, which will install to the hard disk that you specify with your desired network card, partitions, etc.

## References:
- Operating Systems: Design and Implementation (3e)
- Minix QD (has Minix 1 and 2, but not the book versions which is what I'm interested in)
