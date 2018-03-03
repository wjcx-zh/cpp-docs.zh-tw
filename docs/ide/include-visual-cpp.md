---
title: "&lt;包含&gt;（Visual c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- include
- <include>
dev_langs:
- C++
helpviewer_keywords:
- include C++ XML tag
- <include> C++ XML tag
ms.assetid: 392a3e61-0371-4617-8362-446650876ce3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f9a6b07ce540d67a44e46a24fb943dac93bb95a4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ltincludegt-visual-c"></a>&lt;包含&gt;（Visual c + +）
\<include> 標記可讓您參考另一個檔案中描述原始程式碼中類型和成員的註解。 這是將文件註解直接放在原始程式碼檔中的替代方案。  例如，您可以使用\<包括 > 插入您的小組或公司使用的標準 「 重複使用 」 註解。  
  
## <a name="syntax"></a>語法  
  
```  
<include file='filename' path='tagpath' />  
```  
  
#### <a name="parameters"></a>參數  
 `filename`  
 包含文件的檔案名稱。 檔案名稱可以使用路徑進行限定。  以單引號或雙引號將名稱括起來。  如果編譯器找不到 `filename`，它會發出警告。  
  
 `tagpath`  
 有效的 XPath 運算式選取檔案中包含所需的節點集。  
  
 `name`  
 標記中位在註解前面的名稱規範；`name` 會有 `id`。  
  
 `id`  
 位在註解前面的標記識別碼。  以單引號或雙引號將名稱括起來。  
  
## <a name="remarks"></a>備註  
 \<include> 標記使用 XML XPath 語法。 請參閱 XPath 的方式使用自訂的文件\<包括 >。  
  
 編譯搭配 [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這是多檔案範例。 第一個檔案，其\<包括 >，包含下列文件註解：  
  
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
  
 第二個檔案 xml_include_tag.doc 包含下列文件註解：  
  
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
  
## <a name="program-output"></a>程式輸出  
  
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
  
## <a name="see-also"></a>請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)