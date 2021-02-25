
# Table of Contents

1.  [Steps](#orgf91e4a2)
    1.  [An eye out:](#org539cbe5)
2.  [Details](#org21fc2d2)



<a id="orgf91e4a2"></a>

# Steps

-   Info about acpi table: `$ acpidump > <file>` then `acpixtract -a > <file>`.

-   Decompile the extracted files: `iasl -d *.dat`.

-   Compile the files again: `iasl -tc *.dsl`. Errors may occur, correct the file and compile again

-   Create a cpio archive with the fixed ACPI table: `find kernel | cpio -H newc --create > acpi_override`

-   Copy the created `acpi_override` file to `/boot` directory.

-   Copy `01_acpi_dsdt` file to your `grub.d` directory

-   Update your grub `grub-mkconfig -o /boot/grub/grub.cfg`


<a id="org539cbe5"></a>

## An eye out:

-   `01_acpi_dsdt` file contains a line pointing to `grub-mkconfig_lib`. The path may change in your system


<a id="org21fc2d2"></a>

# Details

<https://wiki.archlinux.org/index.php/DSDT>

