# ziwei-data

「问星」紫微斗数 13 维解读数据，按年月切分的小文件，供手机端流式加载。

- 上游：[Renhuai123/ziwei-doushu](https://github.com/Renhuai123/ziwei-doushu) `v4.0-13d`
  （`year-1950.jsonl.zst` … `year-2026.jsonl.zst`，单年解压后约 748MB，不适合手机直接加载）
- 本仓库：按 `"m"`（月份）切分为 `data/YYYY/MM.jsonl.zst`，每块约 730 行、raw 约 60MB、zstd 约 2MB
- 每行格式：`{"k":"1995-06-15-6-male","y":1995,"m":6,"d":15,"h":6,"g":"male","ms":"紫微","t":{…},"c":{"overview":"…","personality":"…",…13个维度…}}`
- 客户端：按需 `fetch` 当月文件 → zstd 解压 → 按行查找 `"k":"{key}"` → `JSON.parse(line).c`

## CDN

```
https://cdn.jsdelivr.net/gh/zjeep-arch/ziwei-data@main/data/1995/06.jsonl.zst
```

共 924 个文件（1950–2026 × 12 个月），约 1.7GB。
