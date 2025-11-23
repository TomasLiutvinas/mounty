(Note this was just initial prompt/idea, required a lot of tweaks)

I've got some storage devices.
For example an SD card, external HDDs, a few USB drives.
Usual workflow is doing: 
lsblk -f
mount /dev/sdx /mnt/sdcard (or other folders I've premade for my constant devices like /mnt/12tb /mnt/floki /mnt/dexter /mnt/vbear or just /mnt/temp etc..)
doing some work
doing umount /mnt/sdcard (or whatever)

I'm looking to build a tool that would allow me to:
type in `sudo mounty` (I assume i would need sudo here)
this would fzf show me friendly names of mountable things using `lsblk -l -p -n --output name,size,label, model`
I'd choose what i want to mount
then it would show me a list of what available /mnt/* folders i have (must list only unmounted directories, not recursive single level)
and it would mount it

and then i would need `sudo unmounty`
that would list mounted entries and unmount whatever i choose

I don't have a language preference for the implementation
