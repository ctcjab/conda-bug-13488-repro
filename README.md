# Conda bug 13488

Ref: https://github.com/conda/conda/issues/13488


# Reproduction Steps

1. Copy the `*.partial` files from the `conda_pkgs` directory into the directory you get when you run `conda config --show pkgs_dirs`.

2. Run `conda create -y -n repro --file repro.txt`

3. Observe errors like:

```
Downloading and Extracting Packages:


ChecksumMismatchError: Conda detected a mismatch between the expected content and downloaded content
for url 'https://conda.anaconda.org/conda-forge/noarch/h2-4.1.0-pyhd8ed1ab_0.tar.bz2'.
  download saved to: /ctc/users/bronsonj/conda_pkgs/h2-4.1.0-pyhd8ed1ab_0.tar.bz2
  expected md5: b748fbf7060927a6e82df7cb5ee8f097
  actual md5: 06e758d0ac943ba9c4c3a1fa92ae7ca9

ChecksumMismatchError: Conda detected a mismatch between the expected content and downloaded content
for url 'https://conda.anaconda.org/conda-forge/noarch/h2-4.1.0-pyhd8ed1ab_0.tar.bz2'.
  download saved to: /ctc/users/bronsonj/conda_pkgs/h2-4.1.0-pyhd8ed1ab_0.tar.bz2
  expected md5: b748fbf7060927a6e82df7cb5ee8f097
  actual md5: 06e758d0ac943ba9c4c3a1fa92ae7ca9
```

# Additional context

```
$ conda --version
conda 24.9.2

$ uname -a
Linux myhost 5.14.0-427.33.1.el9_4.x86_64 #1 SMP PREEMPT_DYNAMIC Fri Aug 16 10:56:24 EDT 2024 x86_64 x86_64 x86_64 GNU/Linux

$ df -Th /
Filesystem            Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg00-root ext4  1.8T  566G  1.1T  35% /
```
