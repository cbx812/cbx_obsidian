
# Metadata
---
Date:: {{date}}
Status:: #📦  
Type:: 日记
Person:: [[@SSY]]
Weather:: #🔅
Mood:: #😊

# 今日待办
---
#今日todo
- [ ] 
- [ ] 
- [ ] 

# 提醒事项
---
```dataview
task
from #提醒事项  
```

# 总结
---
## Diary


## Extract





# 今日修改的文件
---
```dataview
table status, type, 花果山袋王
where file.mday=date(today)
where status != "#📦" and type != "日记"
sort status desc
```

