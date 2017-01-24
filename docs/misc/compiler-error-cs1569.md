---
title: "編譯器錯誤 CS1569 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1569"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1569"
ms.assetid: 1d5e89d6-0a05-4e4f-b472-9089146696bb
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1569
產生 XML 文件檔案 'Filename' 時發生錯誤 \('reason'\)  
  
 當您嘗試將 XML 文件寫入訊息中所指定的檔案時，出現指定原因的錯誤。 原因可能類似「找不到網路磁碟機」或「拒絕存取」。 通常在原因中會建議需要執行以更正錯誤的動作。 例如，如果錯誤指出「拒絕存取」，您可以確認是否具有檔案的寫入權限。  
  
## 範例  
  
```  
// 1569a.cs // compile with: /doc:CS1569.xml // post-build command: attrib +r CS1569.xml class Test { /// <summary>Test.</summary> public static void Main() {} }  
```  
  
## 範例  
 上一個範例會產生 .xml 檔，然後將其設定為唯讀。 這個範例會嘗試寫入同一個檔案。 下列範例會產生 CS1569。  
  
```  
// CS1569.cs // compile with: /doc:CS1569.xml // CS1569 expected class Test { /// <summary>Test.</summary> public static void Main() {} }  
  
```