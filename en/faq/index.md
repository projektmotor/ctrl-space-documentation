# FAQ - Frequently Asked Questions

## Can I use CTRL+SPACE with a 32 bit operating system?

Yes you can! But you will be limited to a maximum CTRL+SPACE project size of less than 4GB due to architectonical reasons.
To get it work you have to change param Xmx to a lower value:

```
# in ./etc/controlspace.conf

# before
default_options=" --branding controlspace -J-Xms1024m -J-Xmx8196m -J-Dnetbeans.logger.console=true -J-ea"

# after
default_options=" --branding controlspace -J-Xms1024m -J-Xmx2048m -J-Dnetbeans.logger.console=true -J-ea"
```
