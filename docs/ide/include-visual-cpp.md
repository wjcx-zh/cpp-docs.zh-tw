---
title: "&lt;include&gt; (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "include"
  - "<include>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<include> C++ XML 標記"
  - "include C++ XML 標記"
ms.assetid: 392a3e61-0371-4617-8362-446650876ce3
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;include&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<include\> 標記讓您參考其他檔案內的註解，這些檔案描述了您原始程式碼中的型別以及成員。  除了將文件註解直接放置在您原始程式碼檔案中，您也可以使用這種方法。  例如，您可以使用 \<include\> 將使用在您的小組或公司中的標準「未定案」註解。  
  
## 語法  
  
```  
<include file='filename' path='tagpath' />  
```  
  
#### 參數  
 `filename`  
 為含有文件的檔案名稱。  可將檔案名稱加上路徑。  將名稱加上單引號或雙引號。  編譯器會發出警告 \(如果找不到 `filename`。  
  
 `tagpath`  
 選取檔案所需的節點集合中包含的有效的 XPath 運算式。  
  
 `name`  
 註解前面標記內的名稱規範。`name` 會有一個 `id`。  
  
 `id`  
 註解前面之標記的 ID。  將名稱加上單引號或雙引號。  
  
## 備註  
 \<include\> 標記使用了 XML XPath 的語法。  使用 \<include\>，參考方式的 XPath 文件可以自訂。  
  
 使用 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
 這是多重檔案的範例。  第一個檔案，請使用 \<include\>，包含下列文件註解:  
  
```  
// xml_include_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_include_tag.dll  
  
/// <include file='xml_include_tag.doc' path='MyDocs/MyMembers[@name="test"]/*' />  
public ref class Test {  
   void TestMethod() {  
   }  
};  
  
/// <include file='xml_include_tag.doc' path='MyDocs/MyMembers[@name="test2"]/*' />  
public ref class Test2 {  
   void Test() {  
   }  
};  
```  
  
 第二個檔案 \(xml\_include\_tag.doc\) 包含下列的文件註解。  
  
```  
<MyDocs>  
  
<MyMembers name="test">  
<summary>  
The summary for this type.  
</summary>  
</MyMembers>  
  
<MyMembers name="test2">  
<summary>  
The summary for this other type.  
</summary>  
</MyMembers>  
  
</MyDocs>  
```  
  
## 程式輸出  
  
```  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>t2</name>  
    </assembly>  
    <members>  
        <member name="T:Test">  
            <summary>  
The summary for this type.  
</summary>  
        </member>  
        <member name="T:Test2">  
            <summary>  
The summary for this other type.  
</summary>  
        </member>  
    </members>  
</doc>  
```  
  
## 請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)