---
title: "&lt;remarks&gt; (Visual C++) | Microsoft Docs"
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
  - "remarks"
  - "<remarks>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<remarks> C++ XML 標記"
  - "remarks C++ XML 標記"
ms.assetid: c820083b-3192-40ab-9ec8-1472c55b4247
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;remarks&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<remarks\> 標記可用於加入型別的相關資訊，補充以 [\<summary\>](../ide/summary-visual-cpp.md) 指定的資訊。  這項資訊會顯示在 [物件瀏覽器](http://msdn.microsoft.com/zh-tw/f89acfc5-1152-413d-9f56-3dc16e3f0470) 和程式碼結構 Web 報告。  
  
## 語法  
  
```  
<remarks>description</remarks>  
```  
  
#### 參數  
 `description`  
 為成員的描述。  
  
## 備註  
 使用 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
  
```  
// xml_remarks_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_remarks_tag.dll  
  
using namespace System;  
  
/// <summary>  
/// You may have some primary information about this class.  
/// </summary>  
/// <remarks>  
/// You may have some additional information about this class.  
/// </remarks>  
public ref class MyClass {};  
```  
  
## 請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)