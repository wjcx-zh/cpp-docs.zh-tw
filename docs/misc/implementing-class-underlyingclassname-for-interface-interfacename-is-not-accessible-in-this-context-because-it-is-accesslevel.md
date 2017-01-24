---
title: "實作介面 &#39;&lt;介面名稱&gt;&#39; 的類別 &#39;&lt;基本類別名稱&gt;&#39; 在這個內容中是不可執行的，因為它是 &#39;&lt;存取層級&gt;&#39; | Microsoft Docs"
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
  - "BC31109"
  - "vbc31109"
helpviewer_keywords: 
  - "BC31109"
ms.assetid: ab2a3bc3-b875-476f-b601-3e736ad2677e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 實作介面 &#39;&lt;介面名稱&gt;&#39; 的類別 &#39;&lt;基本類別名稱&gt;&#39; 在這個內容中是不可執行的，因為它是 &#39;&lt;存取層級&gt;&#39;
介面以指定基本類別的 <xref:System.Runtime.InteropServices.CoClassAttribute> 宣告，但此類別的存取層級卻不得使用程式碼存取。  
  
 將 <xref:System.Runtime.InteropServices.CoClassAttribute> 套用到介面，會讓基本類別和此介面產生關聯。 這會允許程式碼使用 `New` 子句直接從介面建立物件。  
  
 如果使用 `New` 子句的程式碼不能存取基本類別，例如類別是 `Private`，則編譯器就會產生這個錯誤。  
  
 **錯誤 ID：**BC31109  
  
### 更正這個錯誤  
  
1.  如果您有基本類別的原始檔控制，請調整其存取層級，讓使用中的程式碼可以存取它。  
  
2.  如有任何原因無法變更基本類別的存取層級，請移除 `New` 子句。 您無法直接從這個介面建立物件。  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.CoClassAttribute>   
 [New Operator](../Topic/New%20Operator%20\(Visual%20Basic\).md)   
 [Access Levels in Visual Basic](../Topic/Access%20Levels%20in%20Visual%20Basic.md)