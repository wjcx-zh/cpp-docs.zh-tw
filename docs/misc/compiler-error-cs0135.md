---
title: "編譯器錯誤 CS0135 | Microsoft Docs"
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
  - "CS0135"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0135"
ms.assetid: 1bda402c-e8bd-4117-93d9-f4968d9e8303
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0135
'declaration1' 與宣告 'declaration2' 相衝突  
  
 編譯器不允許隱藏名稱，這通常會導致您的程式碼出現邏輯錯誤。  
  
## 範例  
 下列範例會產生 CS0135：  
  
```  
// CS0135.cs  
public class MyClass2  
{  
   public static int i = 0;  
  
   public static void Main()  
   {  
      {  
         int i = 4;  
         i++;  
      }  
      i = 0;   // CS0135  
   }  
}  
```  
  
 擷取自 [C\# 語言規格](../Topic/C%23%20Language%20Specification.md)的 7.5.2.1 小節：  
  
 針對運算式或宣告子中每個出現之指定簡單名稱的識別項，在包圍該出現位置的區域變數宣告空格 \(§3.3\) 中，運算式或宣告子中其他所有出現之指定簡單名稱的相同識別項都必須參考相同的實體。 這項規則可確保某個名稱在指定區塊、switch 區塊、for 陳述式、foreach 陳述式、using 陳述式或匿名函式中一律同義。