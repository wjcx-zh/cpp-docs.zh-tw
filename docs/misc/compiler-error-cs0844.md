---
title: "編譯器錯誤 CS0844 | Microsoft Docs"
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
  - "CS0844"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0844"
ms.assetid: ccf74e01-292a-42d0-897c-8add7aee2118
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0844
在宣告區域變數 'name' 之前無法使用此區域變數。 區域變數的宣告會隱藏欄位 'name'。  
  
 在指定的區塊中，識別項只能有一種意義。 引進識別項的第二種意義，與類別欄位同名的區域變數就可以隱藏欄位。 因此，如果您參照方法中的類別欄位，然後宣告同名的區域變數，則編譯器會產生錯誤。  
  
### 更正這個錯誤  
  
-   使用 `this.num` 來參照類別欄位。  
  
-   為區域變數指定與類別欄位不同的名稱。  
  
## 範例  
 下列程式碼會產生 CS0844：  
  
```  
class Test { int num; public void TestMethod() { num = 5; // CS0844 int num = 6;        } public static int Main() { return 1; } }  
```