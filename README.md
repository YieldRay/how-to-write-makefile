Source: <https://github.com/seisman/how-to-write-makefile>

这里通过一个简单的脚本，通过 pandoc 将 rst 文件转换为 markdown

另外做了若干 typo 修正

```bash
#!/bin/bash

src_dir="source"
dst_dir="dist"

mkdir "$dst_dir"

if [ ! -d "$src_dir" ]; then
    echo "Directory $src_dir does not exist."
    exit 1
fi

for file in "$src_dir"/*.rst; do
    if [ -f "$file" ]; then
        base_name=$(basename -- "$file")
        name_without_ext="${base_name%.rst}"
        output_file="$dst_dir/$name_without_ext.md"

        pandoc "$file" -f rst -t markdown -o "$output_file"
        echo "Converted $file to $output_file"
    fi
done
```

其它参考：<https://github.com/theicfire/makefiletutorial>
