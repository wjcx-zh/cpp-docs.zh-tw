---
title: "&lt;list&gt; (Visual C++) | Microsoft Docs"
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
  - "list"
  - "<list>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<list> C++ XML 標記"
  - "list C++ XML 標記"
ms.assetid: c792a10b-0451-422c-9aa0-604116e69d64
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;list&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<listheader\> 區塊用於定義表格或定義清單的標題列。  在定義表格時，您只需要提供一個詞彙項目做為標題。  
  
## 語法  
  
```  
<list type="bullet" | "number" | "table">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
#### 參數  
 `term`  
 將定義於 `description` 中的詞彙。  
  
 `description`  
 為項目符號、編號清單中的項目或 `term` 的定義其中之一。  
  
## 備註  
 清單中的每個項目都以 \<item\> 區塊來指定。  當建立定義清單時，您必須指定 `term` 和 `description`。  但是對於表格、項目符號清單或編號清單，則只需提供 `description` 的項目。  
  
 在清單或表格中可以有全部需要的 \<item\> 區塊。  
  
 使用 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
  
```  
// xml_list_tag.cpp  
// compile with: /doc /LD  
// post-build command: xdcmake xml_list_tag.dll  
/// <remarks>Here is an example of a bulleted list:  
/// <list type="bullet">  
/// <item>  
/// <description>Item 1.</description>  
/// </item>  
/// <item>  
/// <description>Item 2.</description>  
/// </item>  
/// </list>  
/// </remarks>  
class MyClass {};  
```  
  
## 請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)