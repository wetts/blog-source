在项目开发中，有时提交form表单时不能单单用action或者jQuery的
表单提交方法有三种，主要说下第三种
第一种：用form自带属性action提交
第二种：用jquery提交：$("#formid").submit();
第三种：用ajax提交：
但如果form表单中数据很多时，不可能一一列出，只需要用
$('#yourformid').serialize()就可以了
举例如下：
```
$.ajax({
	cache: true,
	type: "POST",
	url:ajaxCallUrl,
	data:$('#yourformid').serialize(),// 你的formid
	async: false,
	error: function(request) {
		alert("Connection error");
	},
	success: function(data) {
		$("#commonLayout_appcreshi").parent().html(data);\
	}
});
``