行高等于盒子height高度，文字会垂直居中对齐

基线和基线的距离为行高

合并表格相邻边框

```
table, td {
	border-collapse: collapse;
}

```

图片小块和文字对齐方法，设置图片span样式如下，就可以通过margin来调整对齐了

```
span {
	display: inline-block;
	vertical-align: middle;
}
```

