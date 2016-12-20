---
title: "在 &#39;Global&#39; 之後必須跟隨 &#39;.&#39; 及一個識別項。 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36000"
  - "vbc36000"
helpviewer_keywords: 
  - "BC36000"
ms.assetid: 0007d7b4-54a2-4f09-904c-d5ad60a55f8e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在 &#39;Global&#39; 之後必須跟隨 &#39;.&#39; 及一個識別項。
[Global \- delete](http://msdn.microsoft.com/zh-tw/18c8ba14-40f6-4978-8096-6a5852324635) 關鍵字會出現在存取命名空間以外的內容中。  
  
 `Global` 的目的，是可讓您的程式碼從已封鎖根層級命名空間的命名空間結構中存取根層級命名空間。  
  
 **錯誤 ID︰**BC36000  
  
### 更正這個錯誤  
  
-   如果您想要存取根層級命名空間，請在它的後面指定 `Global` 關鍵字和句號 \(`.`\)。  
  
    ```  
    Dim keyInfo As Global.System.ConsoleKeyInfo  
    ```  
  
-   如果您不想要存取根層級命名空間，請移除 `Global` 關鍵字。  
  
## 請參閱  
 [Global \- delete](http://msdn.microsoft.com/zh-tw/18c8ba14-40f6-4978-8096-6a5852324635)