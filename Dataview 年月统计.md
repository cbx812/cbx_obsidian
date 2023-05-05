---
metatable: true
vaultPath: "100-文献笔记"
outType: md
searchTag: 
searchCodePro1: 
searchCodePro2: 
searchYear: 2022年
searchMonth: 11月
searchFinish: All
---

```dataviewjs
/*YAML
---
metatable: true
vaultPath: Notes
outType: md
searchTag: 
searchCodePro1: 
searchCodePro2: 
searchYear: 2022年
searchMonth: 11月
searchFinish: All
---
*/
const startTime = new Date().getTime();
const metaeditEnabled = app.plugins.enabledPlugins.has("metaedit");
const thisFile = dv.pages().where((f) => f.file.path == dv.current().file.path);
let outType = dv.current().outType;
let vaultPath = dv.current().vaultPath;
let searchTag = dv.current().searchTag;
let searchCodePro1 = dv.current().searchCodePro1;
let searchCodePro2 = dv.current().searchCodePro2;
let searchYear = dv.current().searchYear;
let searchMonth = dv.current().searchMonth;
let searchFinish = dv.current().searchFinish;
if (metaeditEnabled == true) {
  const { update } = this.app.plugins.plugins["metaedit"].api;
  dv.el("IFPM", "", { cls: "root" });
  if (app.plugins.plugins.dataview.manifest.version.match(/0\.4\./) != null) {
    dv.el(
      "p",
      "🚨 <u>当前 DataView 为 " +
        app.plugins.plugins.dataview.manifest.version +
        " 版本，现在您可更新到最新版本</u>",
      {
        attr: { style: "color:red;font-weight:900;font-size:14px" },
      }
    );
  }
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
  function unique(arr) {
    return Array.from(new Set(arr));
  }
  const outTypeDropdownMaker = (pn, fpath) => {
    const file = this.app.vault.getAbstractFileByPath(fpath);
    const optionsText = ["MD", "CSV"];
    const optionsValue = ["md", "csv"];
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
      ? (dropdown.selectedIndex = optionsValue.indexOf(outType))
      : (dropdown.selectedIndex = 0);
    dropdown.addEventListener("change", async (evt) => {
      evt.preventDefault();
      await update(pn, optionsValue[dropdown.selectedIndex], file);
    });
    return dropdown;
  };
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
  const yearDropdownMaker = (pn, fpath) => {
    const file = this.app.vault.getAbstractFileByPath(fpath);
    const arr = dv.pages().filter((t) => t.file.path.includes(vaultPath))
      .importDate.c.year;
    let years = Array.from(new Set(arr)).sort();
    years = years.map(function (i) {
      return i + "年";
    });
    years.unshift("全部年");
    years.unshift("noyear");
    const dropdown = this.container.createEl("select");
    dropdown.style = "width:8em";
    years.forEach((year, index) => {
      let opt = year;
      let el = dropdown.createEl("option");
      opt != "noyear" ? (el.textContent = opt) : (el.textContent = "选择年份");
      el.value = opt;
      dropdown.appendChild(el);
    });
    years.indexOf(searchYear.toString()) < 0
      ? (dropdown.selectedIndex = 0)
      : (dropdown.selectedIndex = years.indexOf(searchYear.toString()));
    dropdown.addEventListener("change", async (evt) => {
      evt.preventDefault();
      await update(pn, years[dropdown.selectedIndex], file);
    });
    return dropdown;
  };
  const monthDropdownMaker = (pn, fpath) => {
    const file = this.app.vault.getAbstractFileByPath(fpath);
    const arr = dv.pages().filter((t) => t.file.path.includes(vaultPath))
      .importDate.c.month;
    let months = Array.from(new Set(arr)).sort();
    months.unshift();
    months = months.map(function (i) {
      return i + "月";
    });
    months.unshift("全部月");
    months.unshift("nomonth");
    const dropdown = this.container.createEl("select");
    dropdown.style = "width:8em";
    months.forEach((month, index) => {
      let opt = month;
      let el = dropdown.createEl("option");
      opt != "nomonth" ? (el.textContent = opt) : (el.textContent = "选择月份");
      el.value = opt;
      dropdown.appendChild(el);
    });
    months.indexOf(searchMonth.toString()) < 0
      ? (dropdown.selectedIndex = 0)
      : (dropdown.selectedIndex = months.indexOf(searchMonth.toString()));
    dropdown.addEventListener("change", async (evt) => {
      evt.preventDefault();
      await update(pn, months[dropdown.selectedIndex], file);
    });
    return dropdown;
  };
  const tagsDropdownMaker = (pn, fpath) => {
    const file = this.app.vault.getAbstractFileByPath(fpath);
    const arr = dv.pages().filter((t) => t.file.path.includes(vaultPath))
      .file.tags;
    let tags = Array.from(new Set(arr)).sort();
    tags.unshift("#");
    tags = unique(tags);
    const dropdown = this.container.createEl("select");
    tags.forEach((tag, index) => {
      let opt = tag;
      let el = dropdown.createEl("option");
      opt != "#" ? (el.textContent = opt) : (el.textContent = "全部标签");
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
  const tag1DropdownMaker = (pn, fpath) => {
    const file = this.app.vault.getAbstractFileByPath(fpath);
    const arr = dv.pages().filter((t) => t.file.path.includes(vaultPath))
      .file.tags;
    let tags = Array.from(new Set(arr)).sort();
    tags.unshift("#");
    tags = unique(tags);
    const dropdown = this.container.createEl("select");
    tags.forEach((tag, index) => {
      let opt = tag;
      let el = dropdown.createEl("option");
      opt != "#" ? (el.textContent = opt) : (el.textContent = "全部标签");
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
  const tag2DropdownMaker = (pn, fpath) => {
    const file = this.app.vault.getAbstractFileByPath(fpath);
    const arr = dv.pages().filter((t) => t.file.path.includes(vaultPath))
      .file.tags;
    let tags = Array.from(new Set(arr)).sort();
    tags.unshift("#");
    tags = unique(tags);
    const dropdown = this.container.createEl("select");
    tags.forEach((tag, index) => {
      let opt = tag;
      let el = dropdown.createEl("option");
      opt != "#" ? (el.textContent = opt) : (el.textContent = "全部标签");
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
  const FinishDropdownMaker = (pn, fpath) => {
    const file = this.app.vault.getAbstractFileByPath(fpath);
    const optionsText = ["全部", "已读", "在读", "未读"];
    const optionsValue = ["All", "Done", "reading", "unread"];
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
    dropdown.selectedIndex != null
      ? (dropdown.selectedIndex = optionsValue.indexOf(searchFinish.toString()))
      : (dropdown.selectedIndex = 0);
    dropdown.addEventListener("change", async (evt) => {
      evt.preventDefault();
      await update(pn, optionsValue[dropdown.selectedIndex], file);
    });
    return dropdown;
  };
  dv.el("IFPM", "", { cls: "importDate" });
  dv.el("b", "检索路径:&emsp;&ensp;");
  vaultPathDropdownMaker("vaultPath", dv.current().file.path);
  dv.el("br");
  dv.el("b", "检索时间:&emsp;&ensp;");
  yearDropdownMaker("searchYear", dv.current().file.path);
  dv.el("b", "&emsp;");
  monthDropdownMaker("searchMonth", dv.current().file.path);
  dv.el("br");
  dv.el("b", "阅读状态:&emsp;&ensp;");
  FinishDropdownMaker("searchFinish", dv.current().file.path);
  dv.el("br", "");
  dv.el("b", "选择标签1:&emsp;");
  tagsDropdownMaker("searchTag", dv.current().file.path);
  dv.el("br", "");
  dv.el("b", "选择标签2:&emsp;");
  tag1DropdownMaker("searchCodePro1", dv.current().file.path);
  dv.el("br", "");
  dv.el("b", "选择标签3:&emsp;");
  tag2DropdownMaker("searchCodePro2", dv.current().file.path);
  if (app.isMobile == false) {
    dv.el("br", "");
    dv.el("b", "导出格式:&emsp;&ensp;");
    outTypeDropdownMaker("outType", dv.current().file.path);
  }
  let searchQuery = "outputs = dv.pages()";
  if (searchMonth != "nomonth" && searchYear != "noyear") {
    if (searchMonth != "全部月" && searchYear != "全部年") {
      searchYear = parseInt(searchYear);
      searchMonth = parseInt(searchMonth);
      searchQuery +=
        ".filter((t) =>new Date(t.importDate).getFullYear()==" +
        searchYear +
        " && new Date(t.importDate).getMonth()+1==" +
        searchMonth +
        ")";
      searchYear = dv.current().searchYear;
      searchMonth = dv.current().searchMonth;
    } else if (searchMonth == "全部月" && searchYear != "全部年") {
      searchYear = parseInt(searchYear);
      searchMonth = "";
      searchQuery +=
        ".filter((t) =>new Date(t.importDate).getFullYear()==" +
        searchYear +
        ")";
      searchYear = dv.current().searchYear;
    } else if (searchMonth != "全部月" && searchYear == "全部年") {
      searchYear = "";
      searchMonth = parseInt(searchMonth);
      searchQuery +=
        ".filter((t) =>new Date(t.importDate).getMonth()+1==" +
        searchMonth +
        ")";
      searchMonth = dv.current().searchMonth;
    } else if (searchMonth == "全部月" && searchYear == "全部年") {
      searchYear = "";
      searchMonth = "";
      searchQuery += ".filter((t) =>t.importDate)";
    }
    if (searchTag != null && searchCodePro1 != null && searchCodePro2 != null) {
      searchQuery +=
        ".filter((b) => b.file.tags.indexOf('#'+'" +
        searchTag +
        "') != -1)" +
        ".filter((b) => b.file.tags.indexOf('#'+'" +
        searchCodePro1 +
        "') != -1)" +
        ".filter((b) => b.file.tags.indexOf('#'+'" +
        searchCodePro2 +
        "') != -1)";
      searchTag =
        "含有" +
        " #" +
        searchTag +
        " #" +
        searchCodePro1 +
        " #" +
        searchCodePro2 +
        " 标签的文献";
    } else if (
      searchTag != null &&
      searchCodePro1 != null &&
      searchCodePro2 == null
    ) {
      searchQuery +=
        ".filter((b) => b.file.tags.indexOf('#'+'" +
        searchTag +
        "') != -1)" +
        ".filter((b) => b.file.tags.indexOf('#'+'" +
        searchCodePro1 +
        "') != -1)";
      searchTag =
        "含有" + " #" + searchTag + " #" + searchCodePro1 + " 标签的文献";
    } else if (
      searchTag != null &&
      searchCodePro1 == null &&
      searchCodePro2 != null
    ) {
      searchQuery +=
        ".filter((b) => b.file.tags.indexOf('#'+'" +
        searchTag +
        "') != -1)" +
        ".filter((b) => b.file.tags.indexOf('#'+'" +
        searchCodePro2 +
        "') != -1)";
      searchTag =
        "含有" + " #" + searchTag + " #" + searchCodePro2 + " 标签的文献";
    } else if (
      searchTag != null &&
      searchCodePro1 == null &&
      searchCodePro2 == null
    ) {
      searchQuery +=
        ".filter((b) => b.file.tags.indexOf('#'+'" + searchTag + "') != -1)";
      searchTag = "含有" + " #" + searchTag + " 标签的文献";
    } else if (
      searchTag == null &&
      searchCodePro1 != null &&
      searchCodePro2 != null
    ) {
      searchQuery +=
        ".filter((b) => b.file.tags.indexOf('#'+'" +
        searchCodePro1 +
        "') != -1)" +
        ".filter((b) => b.file.tags.indexOf('#'+'" +
        searchCodePro2 +
        "') != -1)";
      searchTag =
        "含有" + " #" + searchCodePro1 + " #" + searchCodePro2 + " 标签的文献";
    } else if (
      searchTag == null &&
      searchCodePro1 != null &&
      searchCodePro2 == null
    ) {
      searchQuery +=
        ".filter((b) => b.file.tags.indexOf('#'+'" +
        searchCodePro1 +
        "') != -1)";
      searchTag = "含有" + " #" + searchCodePro1 + " 标签的文献";
    } else if (
      searchTag == null &&
      searchCodePro1 == null &&
      searchCodePro2 != null
    ) {
      searchQuery +=
        ".filter((b) => b.file.tags.indexOf('#'+'" +
        searchCodePro2 +
        "') != -1)";
      searchTag = "含有" + " #" + searchCodePro2 + " 标签的文献";
    } else if (
      searchTag == null &&
      searchCodePro1 == null &&
      searchCodePro2 == null
    ) {
      searchTag = "";
    }
    if (searchFinish == "All") {
      searchQuery += "";
    } else {
      searchQuery +=
        ".filter((t) => t.file.tags.toString().includes('" +
        searchFinish +
        "'))";
    }
    if (vaultPath == "") {
      searchQuery += "";
    } else {
      searchQuery +=
        ".filter((t) => t.file.folder.includes('" + vaultPath + "'))";
    }
    let outputs = "";
    eval(searchQuery);
    if (searchFinish == "All") {
      searchFinish = "共导出" + searchTag + "【" + outputs.length + "】篇";
    }
    if (searchFinish == "Done") {
      searchFinish = "已读完" + searchTag + "【" + outputs.length + "】篇";
    }
    if (searchFinish == "reading") {
      searchFinish = "正在阅读" + searchTag + "【" + outputs.length + "】篇";
    }
    if (searchFinish == "unread") {
      searchFinish = "有【" + outputs.length + "】篇" + searchTag + "尚未读过";
    }
    dv.paragraph("#### " + searchYear + searchMonth + "</br>" + searchFinish);
    outputs = outputs.map((b) => [
      b.file.link,
      b.shortTitle,
      b.publicationTitle,
      b.file.tags.values.join(" "),
    ]);
    let title = ["文献笔记", "中文标题", "刊名", "标签"];
    if (app.isMobile == false) {
      let exportButton = document.createElement("a");
      let content;
      if (outType == "md") {
        content =
          "> [!info] <center>" +
          searchYear +
          searchMonth +
          "</br>" +
          searchFinish +
          "</center>\n\n";
        for (let i = 0; i < outputs.length; i++) {
          content += "> [!note]+ " + outputs[i][0] + "\n>> |||\n>> |--:|--|\n";
          for (let z = 1; z < outputs[i].length; z++) {
            content +=
              ">> |<div style='width:5em'>" +
              title[z] +
              "</div>|" +
              outputs[i][z] +
              "|\n";
          }
          content += "\n";
        }
        exportButton.download = "IFPM Export " + getTime() + ".md";
      } else if (outType == "csv") {
        content = title.join(",") + "\n";
        for (let i = 0; i < outputs.length; i++) {
          content += '"' + outputs[i].join('","') + '"\n';
        }
        content = "\ufeff" + content;
        exportButton.download = "IFPM Export " + getTime() + ".csv";
        dv.el(
          "center",
          "🚨 <u>CSV 导出默认为</u> `utf-8 BOM` <u>编码格式如数据分析使用请根据实际需要转换文件编码</u>",
          {
            attr: { style: "color:red;font-weight:900;font-size:14px" },
          }
        );
      }
      let ba64 =
        "data:text/plain;base64," +
        Buffer.from(content, "utf-8").toString("base64");
      exportButton.innerHTML = "点击导出";
      exportButton.href = ba64;
      dv.el("br", "");
      dv.el("center", exportButton, { cls: "exportButton" });
    }
    dv.el("br", "");
    dv.table(title, outputs);
  } else {
    dv.el("br");
    dv.el("br");
    dv.el("b", "### 请完成选择");
  }
} else {
  dv.el("br", "");
  dv.el("b", "# 请安装并启用插件【MetaEdit】");
}
const endTime = new Date().getTime();
console.log("IFPM-ImportDate 运行耗时:" + (endTime - startTime) + "ms");