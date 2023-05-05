---
metatable: true
vaultPath: "100-文献笔记"
searchType: tags
searchText: flexible
searchColor: All
searchTag: 
searchCodePro0: i
searchCodePro1: r
searchCodePro2: y
searchCodePro3: i
---

```dataviewjs
/*YAML
---
# 通用参数
metatable: true
vaultPath: Notes
searchType: tags
searchText: flexible
searchColor: All
searchTag: 
searchCodePro0: i
searchCodePro1: r
searchCodePro2: y
searchCodePro3: i
---
*/
///基础定义
let TimeList = {};
let timeCount = 0;
TimeList["Time0"] = new Date().getTime();
function TimeMonitor() {
  timeCount += 1;
  TimeList["Time" + timeCount] = new Date().getTime();
  console.log("Step " + timeCount.toString() + " --> " + (TimeList["Time" + timeCount] - TimeList["Time" + (timeCount - 1)]).toString() + " ms");
}
const metaeditEnabled = app.plugins.enabledPlugins.has("metaedit");
const thisFile = dv.pages().where((f) => f.file.path == dv.current().file.path);
///YAML数据
let vaultPath = dv.current().vaultPath;
let searchTag = dv.current().searchTag;
let searchCodePro1 = dv.current().searchCodePro1;
let searchCodePro2 = dv.current().searchCodePro2;
let searchType = dv.current().searchType;
let searchText = dv.current().searchText;
let searchColor = dv.current().searchColor;
let searchCodePro0 = dv.current().searchCodePro0;
let searchCodePro3 = dv.current().searchCodePro3;
///插件判定
if (metaeditEnabled == true) {
  ///拉取metaeditapi
  const { update } = this.app.plugins.plugins["metaedit"].api;
  dv.el("IFPM", "", { cls: "root" });
  ///Warning
  ///DataView
  if (app.plugins.plugins.dataview.manifest.version.match(/0\.4\./) != null) {
    dv.el(
      "p",
      "🚨 <u>当前 DataView 为 " +
      app.plugins.plugins.dataview.manifest.version +
      "版本,为避免不必要的麻烦，建议更新为最新版本</u>",
      {
        attr: { style: "color:red;font-weight:900;font-size:14px" },
      }
    );
  }
  ///Tips
  ///CSS版本判断提示
  let cssOn = 0;
  for (let i = 0; i < app.customCss.extraStyleEls.length; i++) {
    if (
      app.customCss.extraStyleEls[i].innerText.indexOf(
        "/*--DKLN-V1.3.2-IFPM--*/"
      ) != -1
    ) {
      cssOn += 1;
    }
  }
  if (cssOn == 0) {
    dv.el("p", "❇️ 搭配【最新版 IF Pro Max 配套 CSS 片段】使用效果更佳", {
      attr: { style: "color:aqua;font-size:14px" },
    });
  }
  ///通用function
  ///获取当前时间并补位格式化
  function getTime() {
    let time = new Date();
    let year = time.getFullYear();
    let month = time.getMonth() + 1;
    let date = time.getDate();
    let hour = time.getHours();
    let minute = time.getMinutes();
    let second = time.getSeconds();
    function timeAdd0(m) {
      return m < 10 ? "0" + m : m;
    }
    return (
      year +
      "-" +
      timeAdd0(month) +
      "-" +
      timeAdd0(date) +
      " " +
      timeAdd0(hour) +
      "_" +
      timeAdd0(minute) +
      "_" +
      timeAdd0(second)
    );
  }
  ///路径选择器
  const vaultPathDropdownMaker = (pn, fpath) => {
    const file = this.app.vault.getAbstractFileByPath(fpath);
    const arr = dv.pages().file.folder;
    let paths = Array.from(new Set(arr)).sort();
    let z = [];
    for (let i = 0; i < paths.length; i++) {
      if (paths[i] != "" && paths[i] != null) {
        z.push(paths[i]);
      }
    }
    paths = z;
    paths.unshift('""');
    const dropdown = this.container.createEl("select");
    paths.forEach((path, index) => {
      let opt = path;
      let el = dropdown.createEl("option");
      opt != '""' ? (el.textContent = opt) : (el.textContent = "全库检索");
      el.value = opt;
      dropdown.appendChild(el);
    });
    paths.indexOf(vaultPath.toString()) < 0
      ? (dropdown.selectedIndex = 0)
      : (dropdown.selectedIndex = paths.indexOf(vaultPath.toString()));
    dropdown.addEventListener("change", async (evt) => {
      evt.preventDefault();
      await update(pn, paths[dropdown.selectedIndex], file);
    });
    return dropdown;
  };
  ///检索类型选择器
  const searchTypeDropdownMaker = (pn, fpath) => {
    const file = this.app.vault.getAbstractFileByPath(fpath);
    const optionsText = ["标签", "颜色", "图库", "搜索", "生词语料", "高级检索"];
    const optionsValue = ["tags", "color", "image", "searchText", "searchWordLines", "searchpro"];
    const dropdown = this.container.createEl("select");
    const option1 = dropdown.createEl("option");
    option1.text = optionsText[0];
    option1.value = optionsValue[0];
    const option2 = dropdown.createEl("option");
    option2.text = optionsText[1];
    option2.value = optionsValue[1];
    const option3 = dropdown.createEl("option");
    option3.text = optionsText[2];
    option3.value = optionsValue[2];
    const option4 = dropdown.createEl("option");
    option4.style = "text-align: left;";
    option4.text = optionsText[3];
    option4.value = optionsValue[3];
    const option5 = dropdown.createEl("option");
    option5.style = "text-align: left;";
    option5.text = optionsText[4];
    option5.value = optionsValue[4];
    const option6 = dropdown.createEl("option");
    option6.style = "text-align: left;";
    option6.text = optionsText[5];
    option6.value = optionsValue[5];
    dropdown.selectedIndex != null
      ? (dropdown.selectedIndex = optionsValue.indexOf(searchType))
      : (dropdown.selectedIndex = 0);
    dropdown.addEventListener("change", async (evt) => {
      evt.preventDefault();
      await update(pn, optionsValue[dropdown.selectedIndex], file);
    });
    return dropdown;
  };
  ///颜色选择器
  const searchColorDropdownMaker = (pn, fpath) => {
    const file = this.app.vault.getAbstractFileByPath(fpath);
    const optionsText = ["全色", "红色", "黄色", "蓝色", "绿色", "紫色"];
    const optionsValue = [
      "All",
      "ff6666",
      "ffd400",
      "2ea8e5",
      "5fb236",
      "a28ae5",
    ];
    const dropdown = this.container.createEl("select");
    dropdown.style = "width:6em;text-align:center";
    const option1 = dropdown.createEl("option");
    option1.style = "text-align: left;";
    option1.text = optionsText[0];
    option1.value = optionsValue[0];
    const option2 = dropdown.createEl("option");
    option2.style = "text-align: left;";
    option2.text = optionsText[1];
    option2.value = optionsValue[1];
    const option3 = dropdown.createEl("option");
    option3.style = "text-align: left;";
    option3.text = optionsText[2];
    option3.value = optionsValue[2];
    const option4 = dropdown.createEl("option");
    option4.style = "text-align: left;";
    option4.text = optionsText[3];
    option4.value = optionsValue[3];
    const option5 = dropdown.createEl("option");
    option5.style = "text-align: left;";
    option5.text = optionsText[4];
    option5.value = optionsValue[4];
    const option6 = dropdown.createEl("option");
    option6.style = "text-align: left;";
    option6.text = optionsText[5];
    option6.value = optionsValue[5];
    dropdown.selectedIndex != null
      ? (dropdown.selectedIndex = optionsValue.indexOf(searchColor))
      : (dropdown.selectedIndex = 0);
    dropdown.addEventListener("change", async (evt) => {
      evt.preventDefault();
      await update(pn, optionsValue[dropdown.selectedIndex], file);
    });
    return dropdown;
  };
  ///进阶检索颜色1
  const searchCodePro1DropdownMaker = (pn, fpath) => {
    const file = this.app.vault.getAbstractFileByPath(fpath);
    const optionsText = ["全色", "红色", "黄色", "蓝色", "绿色", "紫色"];
    const optionsValue = ["a", "r", "y", "b", "g", "p"];
    const dropdown = this.container.createEl("select");
    dropdown.style = "width:6em;text-align:center";
    const option1 = dropdown.createEl("option");
    option1.style = "text-align: left;";
    option1.text = optionsText[0];
    option1.value = optionsValue[0];
    const option2 = dropdown.createEl("option");
    option2.style = "text-align: left;";
    option2.text = optionsText[1];
    option2.value = optionsValue[1];
    const option3 = dropdown.createEl("option");
    option3.style = "text-align: left;";
    option3.text = optionsText[2];
    option3.value = optionsValue[2];
    const option4 = dropdown.createEl("option");
    option4.style = "text-align: left;";
    option4.text = optionsText[3];
    option4.value = optionsValue[3];
    const option5 = dropdown.createEl("option");
    option5.style = "text-align: left;";
    option5.text = optionsText[4];
    option5.value = optionsValue[4];
    const option6 = dropdown.createEl("option");
    option6.style = "text-align: left;";
    option6.text = optionsText[5];
    option6.value = optionsValue[5];
    dropdown.selectedIndex != null
      ? (dropdown.selectedIndex = optionsValue.indexOf(searchCodePro1))
      : (dropdown.selectedIndex = 0);
    dropdown.addEventListener("change", async (evt) => {
      evt.preventDefault();
      await update(pn, optionsValue[dropdown.selectedIndex], file);
    });
    return dropdown;
  };
  ///进阶检索颜色2
  const searchCodePro2DropdownMaker = (pn, fpath) => {
    const file = this.app.vault.getAbstractFileByPath(fpath);
    const optionsText = ["全色", "红色", "黄色", "蓝色", "绿色", "紫色"];
    const optionsValue = ["a", "r", "y", "b", "g", "p"];
    const dropdown = this.container.createEl("select");
    dropdown.style = "width:6em;text-align:center";
    const option1 = dropdown.createEl("option");
    option1.style = "text-align: left;";
    option1.text = optionsText[0];
    option1.value = optionsValue[0];
    const option2 = dropdown.createEl("option");
    option2.style = "text-align: left;";
    option2.text = optionsText[1];
    option2.value = optionsValue[1];
    const option3 = dropdown.createEl("option");
    option3.style = "text-align: left;";
    option3.text = optionsText[2];
    option3.value = optionsValue[2];
    const option4 = dropdown.createEl("option");
    option4.style = "text-align: left;";
    option4.text = optionsText[3];
    option4.value = optionsValue[3];
    const option5 = dropdown.createEl("option");
    option5.style = "text-align: left;";
    option5.text = optionsText[4];
    option5.value = optionsValue[4];
    const option6 = dropdown.createEl("option");
    option6.style = "text-align: left;";
    option6.text = optionsText[5];
    option6.value = optionsValue[5];
    dropdown.selectedIndex != null
      ? (dropdown.selectedIndex = optionsValue.indexOf(searchCodePro2))
      : (dropdown.selectedIndex = 0);
    dropdown.addEventListener("change", async (evt) => {
      evt.preventDefault();
      await update(pn, optionsValue[dropdown.selectedIndex], file);
    });
    return dropdown;
  };
  ///进阶基础模式选择器
  const searchCodePro3DropdownMaker = (pn, fpath) => {
    const file = this.app.vault.getAbstractFileByPath(fpath);
    const optionsText = ["图", "标签"];
    const optionsValue = ["i", "t"];
    const dropdown = this.container.createEl("select");
    dropdown.style = "width:6em;text-align:center";
    const option1 = dropdown.createEl("option");
    option1.style = "text-align: left;";
    option1.text = optionsText[0];
    option1.value = optionsValue[0];
    const option2 = dropdown.createEl("option");
    option2.style = "text-align: left;";
    option2.text = optionsText[1];
    option2.value = optionsValue[1];
    dropdown.selectedIndex != null
      ? (dropdown.selectedIndex = optionsValue.indexOf(searchCodePro3))
      : (dropdown.selectedIndex = 0);
    dropdown.addEventListener("change", async (evt) => {
      evt.preventDefault();
      await update(pn, optionsValue[dropdown.selectedIndex], file);
    });
    return dropdown;
  };
  ///进阶文本关键字检索
  const inputMaker = (pn, input_value, fpath) => {
    const file = this.app.vault.getAbstractFileByPath(fpath);
    const input = this.container.createEl("input");
    input.setAttribute("name", "input");
    input.setAttribute("id", pn);
    input.setAttribute("placeholder", "输入后回车生效");
    input.setAttribute("value", input_value);
    input.addEventListener("keyup", async function (event) {
      event.preventDefault();
      if (event.keyCode === 13) {
        await update(pn, this.value, file);
      }
    });
    return input;
  };
  ///进阶附加模式选择器
  const searchCodePro0DropdownMaker = (pn, fpath) => {
    const file = this.app.vault.getAbstractFileByPath(fpath);
    const optionsText = ["图", "注释", "标签"];
    const optionsValue = ["i", "n", "t"];
    const dropdown = this.container.createEl("select");
    dropdown.style = "width:6em;text-align:center";
    const option1 = dropdown.createEl("option");
    option1.style = "text-align: left;";
    option1.text = optionsText[0];
    option1.value = optionsValue[0];
    const option2 = dropdown.createEl("option");
    option2.style = "text-align: left;";
    option2.text = optionsText[1];
    option2.value = optionsValue[1];
    const option3 = dropdown.createEl("option");
    option3.style = "text-align: left;";
    option3.text = optionsText[2];
    option3.value = optionsValue[2];
    dropdown.selectedIndex != null
      ? (dropdown.selectedIndex = optionsValue.indexOf(searchCodePro0))
      : (dropdown.selectedIndex = 0);
    dropdown.addEventListener("change", async (evt) => {
      evt.preventDefault();
      await update(pn, optionsValue[dropdown.selectedIndex], file);
    });
    return dropdown;
  };
  ///标签选择器
  const tagsDropdownMaker = (pn, fpath) => {
    const file = this.app.vault.getAbstractFileByPath(fpath);
    const arr = dv.pages().filter((t) => t.file.path.includes(vaultPath))
      .file.tags;
    const tags = Array.from(new Set(arr))
      .filter((t) => t.includes("📝/"))
      .sort((a, b) => { return a.localeCompare(b, "zh"); });
    tags.unshift("#");
    const dropdown = this.container.createEl("select");
    tags.forEach((tag, index) => {
      let opt = tag;
      let el = dropdown.createEl("option");
      opt != "#" ? (el.textContent = opt) : (el.textContent = "全部注释标签");
      el.value = opt;
      dropdown.appendChild(el);
    });
    tags.indexOf("#" + searchTag) < 0
      ? (dropdown.selectedIndex = 0)
      : (dropdown.selectedIndex = tags.indexOf("#" + searchTag));
    dropdown.addEventListener("change", async (evt) => {
      evt.preventDefault();
      await update(pn, tags[dropdown.selectedIndex].slice(1), file);
    });
    return dropdown;
  };
  /// 生词语料
  const searchWordLinesMaker = (pn, fpath) => {
    const file = this.app.vault.getAbstractFileByPath(fpath);
    const arr = dv.pages().filter((t) => t.file.path.includes(vaultPath))
      .file.tags;
    const tags = Array.from(new Set(arr))
      .filter((t) => t.includes("🔠/"))
      .sort((a, b) => { return a.localeCompare(b, "zh"); });
    tags.unshift("#");
    const dropdown = this.container.createEl("select");
    tags.forEach((tag, index) => {
      let opt = tag;
      let el = dropdown.createEl("option");
      opt != "#" ? (el.textContent = opt) : (el.textContent = "全部生词语料");
      el.value = opt;
      dropdown.appendChild(el);
    });
    tags.indexOf("#" + searchTag) < 0
      ? (dropdown.selectedIndex = 0)
      : (dropdown.selectedIndex = tags.indexOf("#" + searchTag));
    dropdown.addEventListener("change", async (evt) => {
      evt.preventDefault();
      await update(pn, tags[dropdown.selectedIndex].slice(1), file);
    });
    return dropdown;
  };
  ///进阶笔记标签选择器1
  const tag1DropdownMaker = (pn, fpath) => {
    const file = this.app.vault.getAbstractFileByPath(fpath);
    const arr = dv.pages().filter((t) => t.file.path.includes(vaultPath))
      .file.tags;
    const tags = Array.from(new Set(arr))
      .filter((t) => t.includes("📝/"))
      .sort((a, b) => { return a.localeCompare(b, "zh"); });
    tags.unshift("#");
    const dropdown = this.container.createEl("select");
    tags.forEach((tag, index) => {
      let opt = tag;
      let el = dropdown.createEl("option");
      opt != "#" ? (el.textContent = opt) : (el.textContent = "全部注释标签");
      el.value = opt;
      dropdown.appendChild(el);
    });
    tags.indexOf("#" + searchCodePro1) < 0
      ? (dropdown.selectedIndex = 0)
      : (dropdown.selectedIndex = tags.indexOf("#" + searchCodePro1));
    dropdown.addEventListener("change", async (evt) => {
      evt.preventDefault();
      await update(pn, tags[dropdown.selectedIndex].slice(1), file);
    });
    return dropdown;
  };
  ///进阶笔记标签选择器2
  const tag2DropdownMaker = (pn, fpath) => {
    const file = this.app.vault.getAbstractFileByPath(fpath);
    const arr = dv.pages().filter((t) => t.file.path.includes(vaultPath))
      .file.tags;
    const tags = Array.from(new Set(arr))
      .filter((t) => t.includes("📝/"))
      .sort((a, b) => { return a.localeCompare(b, "zh"); });
    tags.unshift("#");
    const dropdown = this.container.createEl("select");
    tags.forEach((tag, index) => {
      let opt = tag;
      let el = dropdown.createEl("option");
      opt != "#" ? (el.textContent = opt) : (el.textContent = "全部注释标签");
      el.value = opt;
      dropdown.appendChild(el);
    });
    tags.indexOf("#" + searchCodePro2) < 0
      ? (dropdown.selectedIndex = 0)
      : (dropdown.selectedIndex = tags.indexOf("#" + searchCodePro2));
    dropdown.addEventListener("change", async (evt) => {
      evt.preventDefault();
      await update(pn, tags[dropdown.selectedIndex].slice(1), file);
    });
    return dropdown;
  };
  ///输出渲染
  dv.el("IFPM", "", { cls: "dvcards" });
  dv.el("b", "检索路径:&emsp;");
  vaultPathDropdownMaker("vaultPath", dv.current().file.path);
  dv.el("br", "");
  dv.el("br", "");
  dv.el("b", "检索类型:&emsp;");
  searchTypeDropdownMaker("searchType", dv.current().file.path);
  ///基础检索
  if (
    searchType === "color" ||
    searchType === "tags" ||
    searchType === "image" ||
    searchType === "searchWordLines"
  ) {
    dv.el("br", "");
    dv.el("br", "");
    dv.el("b", "选项:&emsp;&emsp;&emsp;");
  }
  ///检索类型判断
  if (searchType === "tags") {
    tagsDropdownMaker("searchTag", dv.current().file.path);
  } else if (searchType === "searchWordLines") {
    searchWordLinesMaker("searchTag", dv.current().file.path);
  } else if (searchType === "color") {
    searchColorDropdownMaker("searchColor", dv.current().file.path);
  } else if (searchType === "image") {
    searchColorDropdownMaker("searchColor", dv.current().file.path);
  } else if (searchType === "searchText") {
    dv.el("br", "");
    dv.el("br", "");
    dv.el("b", "当前检索文本为:&emsp;");
    inputMaker("searchText", searchText, dv.current().file.path);
  } else if (searchType === "searchpro") {
    dv.el("br", "");
    dv.el("br", "");
    dv.el("b", "基础类型:&emsp;");
    searchCodePro0DropdownMaker("searchCodePro0", dv.current().file.path);
    if (searchCodePro0 == "n") {
      dv.el("br", "");
      dv.el("br", "");
      dv.el("b", "注释颜色:&emsp;");
      searchCodePro1DropdownMaker("searchCodePro1", dv.current().file.path);
    } else if (searchCodePro0 == "i") {
      dv.el("br", "");
      dv.el("br", "");
      dv.el("b", "图片颜色:&emsp;");
      searchCodePro1DropdownMaker("searchCodePro1", dv.current().file.path);
    } else if (searchCodePro0 == "t") {
      dv.el("br", "");
      dv.el("br", "");
      dv.el("b", "选择标签:&emsp;");
      tag1DropdownMaker("searchCodePro1", dv.current().file.path);
    } else {
      dv.el("br", "");
      dv.el("br", "");
      dv.el("b", "--->【请选择支持的选项组合】<---");
    }
    dv.el("br", "");
    dv.el("br", "");
    dv.el("b", "附加类型:&emsp;");
    searchCodePro3DropdownMaker("searchCodePro3", dv.current().file.path);
    if (searchCodePro0 == "t" && searchCodePro3 == "t") {
      dv.el("br", "");
      dv.el("br", "");
      dv.el("b", "选择标签:&emsp;");
      tag2DropdownMaker("searchCodePro2", dv.current().file.path);
    } else if (searchCodePro0 != "t" && searchCodePro3 == "t") {
      dv.el("br", "");
      dv.el("br", "");
      dv.el("b", "选择标签:&emsp;");
      tagsDropdownMaker("searchTag", dv.current().file.path);
    } else if (searchCodePro3 == "i") {
      dv.el("br", "");
      dv.el("br", "");
      dv.el("b", "图片颜色:&emsp;");
      searchCodePro2DropdownMaker("searchCodePro2", dv.current().file.path);
    }
  } else {
    dv.el("br", "");
    dv.el("br", "");
    dv.el("b", "--->【请选择支持的选项组合】<---");
  }
  ///检索式生成
  let sCode = "";
  let sQuery = "";
  let color;
  if (searchColor == "ff6666") {
    color = "红色";
  } else if (searchColor == "ffd400") {
    color = "黄色";
  } else if (searchColor == "5fb236") {
    color = "绿色";
  } else if (searchColor == "2ea8e5") {
    color = "蓝色";
  } else if (searchColor == "a28ae5") {
    color = "紫色";
  }
  if (searchType == "searchText" && searchText != null) {
    if (searchText[0] == "/" && searchText[searchText.length - 1] == "/") {
      sCode = "正则【" + searchText + "】";
      sQuery = 'line.substring(63,).replace(/\\(\\[p.*?(\\)\\))/,"").replace(/<\\/span>/,"").match(' + searchText + 'gi)&&line.includes("> <span class=");';
    } else {
      sCode = "文本【" + searchText + "】";
      sQuery = 'line.substring(63,).replace(/\\(\\[p.*?(\\)\\))/,"").replace(/<\\/span>/,"").toUpperCase().includes("' + searchText + '".toUpperCase())&&line.includes("> <span class=");';
    }
  }
  if (searchType == "color") {
    if (searchColor == "All") {
      sCode = "全部颜色注释";
      sQuery = 'line.includes("background-color: #")';
    } else {
      sCode = "【" + color + "】注释";
      sQuery =
        'line.includes("background-color: #' + dv.current().searchColor + '")';
    }
  }
  if (searchType == "image") {
    if (dv.current().searchColor == "All") {
      sCode = "全部图片";
      sQuery = 'line.includes("image#")';
    } else {
      sCode = "【" + color + "】图片";
      sQuery = 'line.includes("image#' + dv.current().searchColor + '")';
    }
  }
  if (searchType == "tags") {
    if (dv.current().searchTag == null) {
      sCode = "全部含标签的注释";
      sQuery = 'line.includes("🏷️ #📝")&&line.includes("span class=")';
    } else {
      sCode = "含 #" + searchTag + " 标签的注释";
      sQuery =
        'line.includes("#' +
        dv.current().searchTag +
        '")&&line.includes("span class=")';
    }
  } if (searchType == "searchWordLines") {
    if (dv.current().searchTag == null) {
      sCode = "全部语料";
      sQuery = 'line.includes("span class=\\"vocabulary\\"")';
    } else {
      sCode = "标记为 #" + searchTag + " 的生词语料";
      sQuery =
        'line.includes("#' +
        dv.current().searchTag +
        '")&&line.includes("span class=")';
    }
  }
  ///进阶检索检索式
  if (searchType == "searchpro") {
    if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "r" &&
      searchCodePro2 == "a" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #ff6666")||line.includes("image#")';
      sCode = "同时显示红色注释和全色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "y" &&
      searchCodePro2 == "a" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #ffd400")||line.includes("image#")';
      sCode = "同时显示黄色注释和全色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "g" &&
      searchCodePro2 == "a" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #5fb236")||line.includes("image#")';
      sCode = "同时显示绿色注释和全色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "b" &&
      searchCodePro2 == "a" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #2ea8e5")||line.includes("image#")';
      sCode = "同时显示蓝色注释和全色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "r" &&
      searchCodePro2 == "r" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #ff6666")||line.includes("image#ff6666")';
      sCode = "同时显示红色注释和红色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "r" &&
      searchCodePro2 == "y" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #ff6666")||line.includes("image#ffd400")';
      sCode = "同时显示红色注释和黄色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "r" &&
      searchCodePro2 == "g" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #ff6666")||line.includes("image#5fb236")';
      sCode = "同时显示红色注释和绿色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "r" &&
      searchCodePro2 == "b" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #ff6666")||line.includes("image#2ea8e5")';
      sCode = "同时显示红色注释和蓝色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "y" &&
      searchCodePro2 == "r" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #ffd400")||line.includes("image#ff6666")';
      sCode = "同时显示黄色注释和红色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "y" &&
      searchCodePro2 == "y" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #ffd400")||line.includes("image#ffd400")';
      sCode = "同时显示黄色注释和黄色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "y" &&
      searchCodePro2 == "g" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #ffd400")||line.includes("image#5fb236")';
      sCode = "同时显示黄色注释和绿色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "y" &&
      searchCodePro2 == "b" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #ffd400")||line.includes("image#2ea8e5")';
      sCode = "同时显示黄色注释和蓝色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "g" &&
      searchCodePro2 == "r" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #5fb236")||line.includes("image#ff6666")';
      sCode = "同时显示绿色注释和红色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "g" &&
      searchCodePro2 == "y" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #5fb236")||line.includes("image#ffd400")';
      sCode = "同时显示绿色注释和黄色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "g" &&
      searchCodePro2 == "g" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #5fb236")||line.includes("image#5fb236")';
      sCode = "同时显示绿色注释和绿色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "g" &&
      searchCodePro2 == "b" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #5fb236")||line.includes("image#2ea8e5")';
      sCode = "同时显示绿色注释和蓝色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "b" &&
      searchCodePro2 == "r" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #2ea8e5")||line.includes("image#ff6666")';
      sCode = "同时显示蓝色注释和红色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "b" &&
      searchCodePro2 == "y" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #2ea8e5")||line.includes("image#ffd400")';
      sCode = "同时显示蓝色注释和黄色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "b" &&
      searchCodePro2 == "g" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #2ea8e5")||line.includes("image#5fb236")';
      sCode = "同时显示蓝色注释和绿色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "b" &&
      searchCodePro2 == "b" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #2ea8e5")||line.includes("image#2ea8e5")';
      sCode = "同时显示蓝色注释和蓝色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "a" &&
      searchCodePro2 == "a" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("background-color: #")||line.includes("image#")';
      sCode = "同时显示全色注释和全色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "a" &&
      searchCodePro2 == "r" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #")||line.includes("image#ff6666")';
      sCode = "同时显示全色注释和红色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "a" &&
      searchCodePro2 == "y" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #")||line.includes("image#ffd400")';
      sCode = "同时显示全色注释和黄色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "a" &&
      searchCodePro2 == "g" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #")||line.includes("image#5fb236")';
      sCode = "同时显示全色注释和绿色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "a" &&
      searchCodePro2 == "b" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #")||line.includes("image#2ea8e5")';
      sCode = "同时显示全色注释和蓝色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "p" &&
      searchCodePro2 == "r" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #a28ae5")||line.includes("image#ff6666")';
      sCode = "同时显示紫色注释和红色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "p" &&
      searchCodePro2 == "y" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #a28ae5")||line.includes("image#ffd400")';
      sCode = "同时显示紫色注释和黄色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "p" &&
      searchCodePro2 == "g" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #a28ae5")||line.includes("image#5fb236")';
      sCode = "同时显示紫色注释和绿色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "p" &&
      searchCodePro2 == "b" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #a28ae5")||line.includes("image#2ea8e5")';
      sCode = "同时显示紫色注释和蓝色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "p" &&
      searchCodePro2 == "p" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #a28ae5")||line.includes("image#a28ae5")';
      sCode = "同时显示紫色注释和紫色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "r" &&
      searchCodePro2 == "p" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #ff6666")||line.includes("image#a28ae5")';
      sCode = "同时显示红色注释和紫色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "y" &&
      searchCodePro2 == "p" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #ffd400")||line.includes("image#a28ae5")';
      sCode = "同时显示黄色注释和紫色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "g" &&
      searchCodePro2 == "p" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #5fb236")||line.includes("image#a28ae5")';
      sCode = "同时显示绿色注释和紫色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "b" &&
      searchCodePro2 == "p" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #2ea8e5")||line.includes("image#a28ae5")';
      sCode = "同时显示蓝色注释和紫色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "a" &&
      searchCodePro2 == "p" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #")||line.includes("image#a28ae5")';
      sCode = "同时显示全色注释和紫色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "p" &&
      searchCodePro2 == "a" &&
      searchCodePro3 == "i"
    ) {
      sQuery =
        'line.includes("background-color: #a28ae5")||line.includes("image#")';
      sCode = "同时显示紫色注释和全色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "r" &&
      searchCodePro2 == "r" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#ff6666")||line.includes("image#ff6666")';
      sCode = "红色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "y" &&
      searchCodePro2 == "r" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#ffd400")||line.includes("image#ff6666")';
      sCode = "同时显示黄色图和红色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "g" &&
      searchCodePro2 == "r" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#5fb236")||line.includes("image#ff6666")';
      sCode = "同时显示绿色图和红色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "b" &&
      searchCodePro2 == "r" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#2ea8e5")||line.includes("image#ff6666")';
      sCode = "同时显示蓝色图和红色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "p" &&
      searchCodePro2 == "r" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#a28ae5")||line.includes("image#ff6666")';
      sCode = "同时显示紫色图和红色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "r" &&
      searchCodePro2 == "y" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#ff6666")||line.includes("image#ffd400")';
      sCode = "同时显示红色图和黄色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "y" &&
      searchCodePro2 == "y" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#ffd400")||line.includes("image#ffd400")';
      sCode = "黄色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "g" &&
      searchCodePro2 == "y" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#5fb236")||line.includes("image#ffd400")';
      sCode = "同时显示绿色图和黄色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "b" &&
      searchCodePro2 == "y" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#2ea8e5")||line.includes("image#ffd400")';
      sCode = "同时显示蓝色图和黄色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "p" &&
      searchCodePro2 == "y" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#a28ae5")||line.includes("image#ffd400")';
      sCode = "同时显示紫色图和黄色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "r" &&
      searchCodePro2 == "g" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#ff6666")||line.includes("image#5fb236")';
      sCode = "同时显示红色图和绿色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "y" &&
      searchCodePro2 == "g" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#ffd400")||line.includes("image#5fb236")';
      sCode = "同时显示黄色图和绿色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "g" &&
      searchCodePro2 == "g" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#5fb236")||line.includes("image#5fb236")';
      sCode = "绿色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "b" &&
      searchCodePro2 == "g" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#2ea8e5")||line.includes("image#5fb236")';
      sCode = "同时显示蓝色图和绿色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "p" &&
      searchCodePro2 == "g" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#a28ae5")||line.includes("image#5fb236")';
      sCode = "同时显示紫色图和绿色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "r" &&
      searchCodePro2 == "b" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#ff6666")||line.includes("image#2ea8e5")';
      sCode = "同时显示红色图和蓝色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "y" &&
      searchCodePro2 == "b" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#ffd400")||line.includes("image#2ea8e5")';
      sCode = "同时显示黄色图和蓝色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "g" &&
      searchCodePro2 == "b" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#5fb236")||line.includes("image#2ea8e5")';
      sCode = "同时显示绿色图和蓝色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "b" &&
      searchCodePro2 == "b" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#2ea8e5")||line.includes("image#2ea8e5")';
      sCode = "蓝色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "p" &&
      searchCodePro2 == "b" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#a28ae5")||line.includes("image#2ea8e5")';
      sCode = "同时显示紫色图和蓝色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "r" &&
      searchCodePro2 == "p" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#ff6666")||line.includes("image#2ea8e5")';
      sCode = "同时显示红色图和紫色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "y" &&
      searchCodePro2 == "p" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#ffd400")||line.includes("image#a28ae5")';
      sCode = "同时显示黄色图和紫色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "g" &&
      searchCodePro2 == "p" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#5fb236")||line.includes("image#a28ae5")';
      sCode = "同时显示绿色图和紫色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "b" &&
      searchCodePro2 == "p" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#2ea8e5")||line.includes("image#a28ae5")';
      sCode = "同时显示蓝色图和紫色图";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "p" &&
      searchCodePro2 == "p" &&
      searchCodePro3 == "i"
    ) {
      sQuery = 'line.includes("image#a28ae5")||line.includes("image#a28ae5")';
      sCode = "紫色图";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "y" &&
      searchTag != null &&
      searchCodePro3 == "t"
    ) {
      sQuery =
        'line.includes("background-color: #ffd400")&&line.includes("#' +
        searchTag +
        '")';
      sCode = "黄色注释且具有 #" + searchTag + " 标签的注释";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "g" &&
      searchTag != null &&
      searchCodePro3 == "t"
    ) {
      sQuery =
        'line.includes("background-color: #5fb236")&&line.includes("#' +
        searchTag +
        '")';
      sCode = "绿色注释且具有 #" + searchTag + " 标签的注释";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "b" &&
      searchTag != null &&
      searchCodePro3 == "t"
    ) {
      sQuery =
        'line.includes("background-color: #2ea8e5")&&line.includes("#' +
        searchTag +
        '")';
      sCode = "蓝色注释且具有 #" + searchTag + " 标签的注释";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "p" &&
      searchTag != null &&
      searchCodePro3 == "t"
    ) {
      sQuery =
        'line.includes("background-color: #a28ae5")&&line.includes("#' +
        searchTag +
        '")';
      sCode = "紫色注释且具有 #" + searchTag + " 标签的注释";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "r" &&
      searchTag != null &&
      searchCodePro3 == "t"
    ) {
      sQuery =
        'line.includes("background-color: #ff6666")&&line.includes("#' +
        searchTag +
        '")';
      sCode = "红色注释且具有 #" + searchTag + " 标签的注释";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "r" &&
      searchTag == "" &&
      searchCodePro3 == "t"
    ) {
      sQuery = 'line.includes("image#ff6666")||line.includes("🏷️ #📝")';
      sCode = "同时显示红色图和所有带标签的注释";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "y" &&
      searchTag == "" &&
      searchCodePro3 == "t"
    ) {
      sQuery = 'line.includes("image#ffd400")||line.includes("🏷️ #📝")';
      sCode = "同时显示黄色图和所有带标签的注释";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "g" &&
      searchTag == "" &&
      searchCodePro3 == "t"
    ) {
      sQuery = 'line.includes("image#5fb236")||line.includes("🏷️ #📝")';
      sCode = "同时显示绿色图和所有带标签的注释";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "b" &&
      searchTag == "" &&
      searchCodePro3 == "t"
    ) {
      sQuery = 'line.includes("image#2ea8e5")||line.includes("🏷️ #📝")';
      sCode = "同时显示蓝色图和所有带标签的注释";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "p" &&
      searchTag == "" &&
      searchCodePro3 == "t"
    ) {
      sQuery = 'line.includes("image#a28ae5")||line.includes("🏷️ #📝")';
      sCode = "同时显示紫色图和所有带标签的注释";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "a" &&
      searchTag == "" &&
      searchCodePro3 == "t"
    ) {
      sQuery = 'line.includes("image#")||line.includes("🏷️ #📝")';
      sCode = "同时显示全色图和所有带标签的注释";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "a" &&
      searchTag == "" &&
      searchCodePro3 == "t"
    ) {
      sQuery = 'line.includes("background-color: #")&&line.includes("🏷️ #📝")';
      sCode = "全部具有 #" + searchTag + " 标签的注释";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "p" &&
      searchTag == "" &&
      searchCodePro3 == "t"
    ) {
      sQuery =
        'line.includes("background-color: #a28ae5")||line.includes("🏷️ #📝")';
      sCode = "同时显示紫色注释和所有带标签的注释";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "y" &&
      searchTag == "" &&
      searchCodePro3 == "t"
    ) {
      sQuery =
        'line.includes("background-color: #ffd400")||line.includes("🏷️ #📝")';
      sCode = "同时显示黄色注释和所有带标签的注释";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "g" &&
      searchTag == "" &&
      searchCodePro3 == "t"
    ) {
      sQuery =
        'line.includes("background-color: #5fb236")||line.includes("🏷️ #📝")';
      sCode = "同时显示绿色注释和所有带标签的注释";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "b" &&
      searchTag == "" &&
      searchCodePro3 == "t"
    ) {
      sQuery =
        'line.includes("background-color: #2ea8e5")||line.includes("🏷️ #📝")';
      sCode = "同时显示蓝色注释和所有带标签的注释";
    } else if (
      searchCodePro0 == "n" &&
      searchCodePro1 == "r" &&
      searchTag == "" &&
      searchCodePro3 == "t"
    ) {
      sQuery =
        'line.includes("background-color: #ff6666")||line.includes("🏷️ #📝")';
      sCode = "同时显示红色注释和所有带标签的注释";
    } else if (
      searchCodePro0 == "t" &&
      searchCodePro2 != null &&
      searchCodePro3 != null &&
      searchCodePro2 != "a" &&
      searchCodePro2 != "r" &&
      searchCodePro2 != "g" &&
      searchCodePro2 != "b" &&
      searchCodePro2 != "y" &&
      searchCodePro2 != "p" &&
      searchCodePro3 != "a" &&
      searchCodePro2 != "r" &&
      searchCodePro3 != "y" &&
      searchCodePro3 != "b" &&
      searchCodePro3 != "g" &&
      searchCodePro3 != "p" &&
      searchCodePro3 == "t"
    ) {
      sQuery =
        'line.includes("#' +
        searchCodePro1 +
        '")&&line.includes("#' +
        searchCodePro2 +
        '")&&line.includes("<span ")';
      sCode =
        "同时具有【" +
        searchCodePro1 +
        "】和【" +
        searchCodePro2 +
        "】标签的注释";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "r" &&
      searchTag != null &&
      searchCodePro3 == "t"
    ) {
      sQuery =
        'line.includes("image#ff6666")&&line.includes("#' + searchTag + '")';
      sCode = "红色且具有 #" + searchTag + " 标签的图片";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "y" &&
      searchTag != null &&
      searchCodePro3 == "t"
    ) {
      sQuery =
        'line.includes("image#ffd400")&&line.includes("#' + searchTag + '")';
      sCode = "黄色且具有 #" + searchTag + " 标签的图片";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "g" &&
      searchTag != null &&
      searchCodePro3 == "t"
    ) {
      sQuery =
        'line.includes("image#5fb236")&&line.includes("#' + searchTag + '")';
      sCode = "绿色且具有 #" + searchTag + " 标签的图片";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "b" &&
      searchTag != null &&
      searchCodePro3 == "t"
    ) {
      sQuery =
        'line.includes("image#2ea8e5")&&line.includes("#' + searchTag + '")';
      sCode = "蓝色且具有 #" + searchTag + " 标签的图片";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "p" &&
      searchTag != null &&
      searchCodePro3 == "t"
    ) {
      sQuery =
        'line.includes("image#a28ae5")&&line.includes("#' + searchTag + '")';
      sCode = "紫色且具有 #" + searchTag + " 标签的图片";
    } else if (
      searchCodePro0 == "i" &&
      searchCodePro1 == "a" &&
      searchTag != null &&
      searchCodePro3 == "t"
    ) {
      sQuery = 'line.includes("image#")&&line.includes("#' + searchTag + '")';
      sCode = "全色且具有 #" + searchTag + " 标签的图片";
    }
  }
  ///检索式判断
  if (sQuery == "") {
    dv.el("br", "");
    dv.el("br", "");
    dv.el("b", "--->【请选择支持的选项组合】<---");
  }
  ///笔记拆分检索计算
  const files = app.vault.getMarkdownFiles();
  let path = files
    .filter((item) => item.parent.path.includes(vaultPath))
    ///暂行Dataview/IFPM屏蔽
    .filter((item) => item.basename.includes("_KEY-") == true)
    .sort(function (x, y) {
      return x.stat.ctime - y.stat.ctime;
    });
  let arr = path.map(async (file) => {
    const content = await app.vault.cachedRead(file);
    let lines = await content.split(/\n\^KEY.{8}\n/).filter((line) => {
      return eval(sQuery);
    });
    ///兼容dataview0.4.*
    if (app.plugins.plugins.dataview.manifest.version.match(/0\.4\./) != null) {
      for (let i = 0; i < lines.length; i++) {
        lines[i] = lines[i] + "</p>";
      }
    }
    return ["[[" + file.basename + "]]", lines];
  });
  ///结果渲染
  Promise.all(arr).then((values) => {
    const exists = values.filter((value) => value[1][0]);
    let outPages = 0;
    for (
      let paperPages = 0;
      paperPages < exists.length;
      paperPages = paperPages + 1
    ) {
      outPages = outPages + exists[paperPages][1].length;
    }
    dv.el("p", "");
    dv.el("b", "检索条件: " + sCode);
    dv.el("br");
    dv.el(
      "b",
      "检索结果: 文献共计 *[" +
      exists.length +
      "]* 篇 笔记共计 *[" +
      outPages +
      "]* 条"
    );
    dv.el("br", "");
    dv.el("br", "");
    ///导出模块
    ///移动端判断
    if (app.isMobile == false) {
      let exportButton = document.createElement("a");
      let content;
      content =
        "> [!info] Meta\n> 检索条件: " +
        sCode +
        "\n> 检索结果: 文献共计 *[" +
        exists.length +
        "]* 篇 笔记共计 *[" +
        outPages +
        "]* 条\n\n";
      for (let z = 0; z < exists.length; z++) {
        content +=
          ">[!note]- " +
          exists[z][0].substring(0, exists[z][0].length - 2) +
          "|" +
          exists[z][0].substring(2, exists[z][0].length - 15) +
          "]]";
        ///兼容dataview0.4.*
        if (
          app.plugins.plugins.dataview.manifest.version.match(/0\.4\./) != null
        ) {
          for (let i = 0; i < exists[z][1].length; i++) {
            exists[z][1][i] = exists[z][1][i].substring(
              0,
              exists[z][1][i].length - 4
            );
            content += exists[z][1][i] + "> ";
            exists[z][1][i] = exists[z][1][i] + "</p>";
          }
          content += "\n\n";
        } else {
          content += exists[z][1].join("> ") + "\n\n";
        }
      }
      let ba64 =
        "data:text/plain;base64," +
        Buffer.from(content, "utf-8").toString("base64");
      exportButton.innerHTML = "导出笔记";
      exportButton.href = ba64;
      exportButton.download = "IFPM Export " + getTime() + ".md";
      dv.el("center", exportButton, { cls: "exportButton" });
      dv.el("br", "");
    }
    ///表格渲染
    dv.table(["文献", "笔记"], exists);
  });
}
///插件不全
else {
  dv.el("br", "");
  dv.el("b", "# 请安装并启用插件【MetaEdit】");
}
TimeMonitor();
console.log("总耗时 " + timeCount.toString() + " --> " + (TimeList["Time" + timeCount] - TimeList["Time0"]).toString() + " ms");
