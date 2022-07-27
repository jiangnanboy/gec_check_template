### grammatical correction
使用纠错模板对中文句子进行语法纠正


#### introduction
模板见resources/zh_template/error_templates_500.txt
```
A,B;1/2/3
```

#### requirements

java11

#### usage
sy/GecCheck

```
        String templatePath = GecCheck.class.getClassLoader().getResource(PropertiesReader.get("template")).getPath().replaceFirst("/", "");
        GecCheck gecRun = new GecCheck();
        gecRun.init(templatePath);
        String sentence;
        while (true) {
            System.out.println("Please input a sentence:");
            Scanner scanner = new Scanner(System.in);
            sentence = scanner.next();
            String infoStr = gecRun.checkCorrect(sentence);
            if(StringUtils.isNotBlank(infoStr)) {
                System.out.println(infoStr);
            }
        }
```

output:

```
爸爸看完小品后忍俊不禁笑了起来。
爸爸看完小品后忍俊不禁。
[{"correct":"忍俊不禁","start":7,"end":15,"error":"忍俊不禁笑了起来"}]

孙中山辞职后不再过问政治，决心尽瘁社会上事业，开始着手社会革命。
孙中山辞职后不再过问政治，决心尽瘁社会上事业，开始社会革命。
[{"correct":"开始","start":23,"end":27,"error":"开始着手"}]

在俄国社会民主工党第二次代表大会中，列宁提出效仿民意党，建立一套围绕少数“职业革命家”为核心、党员对核心高度服从的集权化的组织模式，即民主集中制。
在俄国社会民主工党第二次代表大会中，列宁提出效仿民意党，建立一套少数“职业革命家”为核心、党员对核心高度服从的集权化的组织模式，即民主集中制。
[{"correct":"少数“职业革命家”为核心","start":32,"end":46,"error":"围绕少数“职业革命家”为核心"}]
```

#### contact

如有搜索、推荐、nlp以及大数据挖掘等问题或合作，可联系我：

1、我的github项目介绍：https://github.com/jiangnanboy

2、我的博客园技术博客：https://www.cnblogs.com/little-horse/

3、我的QQ号:2229029156