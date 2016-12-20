---
title: "&#39;&lt;項目名稱&gt;&#39; 無法宣告為 &#39;Partial&#39;，因為部分方法必須是子函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31437"
  - "bc31437"
helpviewer_keywords: 
  - "BC31437"
ms.assetid: 31ca12ab-2c26-4907-a253-e7c57bb4f34b
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;項目名稱&gt;&#39; 無法宣告為 &#39;Partial&#39;，因為部分方法必須是子函式
只有 `Sub` 程序可以宣告為部分方法。 例如，因為 `partialMethod` 是函式，所以下列程式碼會造成這個錯誤：  
  
```  
' Partial Private Function partialMethod(ByVal n As Integer) As Integer ' End Function  
```  
  
 **錯誤 ID：**BC31437  
  
### 更正這個錯誤  
  
-   將您要宣告為部分方法的項目轉換成 `Sub`。  
  
-   這種情況下請勿使用部分方法。  
  
## 請參閱  
 [Partial Methods](../Topic/Partial%20Methods%20\(Visual%20Basic\).md)   
 [Sub Procedures](../Topic/Sub%20Procedures%20\(Visual%20Basic\).md)