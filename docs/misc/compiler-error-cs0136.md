---
title: "編譯器錯誤 CS0136 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0136"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0136"
ms.assetid: 379a1a7d-c52c-4f2b-9e77-c1107d26faf4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0136
無法在此範圍宣告名為 'var' 的區域變數，因為其可能賦予 'var' 不同的意義，而該意義已經於 'parent or current\/child' 範圍中用來代表不同的意義  
  
 變數宣告會隱藏其他可能在範圍內的宣告。 重新命名在產生 CS0136 的行上宣告的變數。  
  
## 範例  
 下列範例會產生 CS0136：  
  
```  
// CS0136.cs  
namespace MyNamespace  
{  
   public class MyClass  
   {  
      public static void Main()  
      {  
         int i = 0;  
         {  
            char i = 'a';   // CS0136, hides int i  
         }  
         i++;  
      }  
   }  
}  
```  
  
 擷取自 [C\# 語言規格](../Topic/C%23%20Language%20Specification.md)的 7.5.2.1 小節：  
  
 針對運算式或宣告子中每個出現之指定簡單名稱的識別項，在包圍該出現位置的區域變數宣告空格 \(§3.3\) 中，運算式或宣告子中其他所有出現之指定簡單名稱的相同識別項都必須參考相同的實體。 這項規則可確保某個名稱在指定區塊、switch 區塊、for 陳述式、foreach 陳述式、using 陳述式或匿名函式中一律同義。