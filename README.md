# tar-extract

## make tar archive

```bash
tar -cf archive.tar ./dir1
```

check
```bash
tar -tf archive.tar 
./dir1/
./dir1/dir2/
./dir1/dir2/dir3/
./dir1/dir2/dir3/001.txt
./dir1/dir2/dir3/002.txt
./dir1/dir2/dir3/003.txt
./dir1/dir2/dir3/004.txt
```

## extract tar archive

### 01: use `--strip=` option

```bash
DST_DIR=tmp
mkdir ${DST_DIR}
tar -xf archive.tar -C ./${DST_DIR} --strip=4
```

### 02: find files

```bash
DST_DIR=tmp
mkdir ${DST_DIR}
tar -xf archive.tar -C ./${DST_DIR}
find ${DST_DIR} -type f | xargs -i mv {} ${DST_DIR}
find ${DST_DIR}/* -type d | xargs -i rm -rf {}
```

