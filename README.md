# work-data-governance

about data governance, such as: irregular operation of contracts, statistics of return visits of enterprises, statistics of business opportunity entry

## Step 1

Make a page load local file (csv file).

1. use input select csv file;
2. use package `csvtojson` covert csv file to json object;
3. 在浏览器端使用 HTML5 `FileReader` 读取文件

```typescript
const handleSelectedFile: ChangeEventHandler<HTMLInputElement> = (e) => {
  const file = e.currentTarget.files?.[0];
  if (file) {
    setFilename(file.name);
    const reader = new FileReader();
    reader.readAsText(file);
    reader.onload = async function (e) {
      const buffer = e.target?.result;
      const content = await csv().fromString(buffer as string);
      setFileContent(content);
    };
  }
};
```
