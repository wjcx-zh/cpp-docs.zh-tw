---
title: "Option Strict 為 On 時，不可進行 &#39;&lt;類型1&gt;&#39; 至 &#39;&lt;類型2&gt;&#39; 的隱含轉換 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30512"
  - "vbc30512"
helpviewer_keywords: 
  - "BC30512"
ms.assetid: b9756d48-05fa-4027-8a80-b4a0ef92099d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict 為 On 時，不可進行 &#39;&lt;類型1&gt;&#39; 至 &#39;&lt;類型2&gt;&#39; 的隱含轉換
您嘗試在類型檢查參數 \([Option Strict Statement](../Topic/Option%20Strict%20Statement.md)\) 設定為 `On` 時，將某個類型轉換成另一個不能包含值的類型，例如將 `Long` 轉換成 `Integer`。  
  
 這種轉換類型稱為*「縮小轉換」*\(narrowing conversion\)，可能會在執行階段失敗。 因此，`Option Strict On` 不允許隱含的縮小轉換。  
  
 **錯誤 ID︰**BC30512  
  
### 更正這個錯誤  
  
1.  判斷是否有從 `<type1>` 到 `<type2>` 的任何類型轉換。 如果兩者都是 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 基礎類型，或兩者都是類別的執行個體，則您通常可以參閱[Widening and Narrowing Conversions](../Topic/Widening%20and%20Narrowing%20Conversions%20\(Visual%20Basic\).md) 中的表格來進行這項判斷。  
  
2.  如果只有從 `<type1>` 到 `<type2>` 的縮小轉換，您應該使用明確轉型。 如果轉換失敗，[CType 函式](../Topic/CType%20Function%20\(Visual%20Basic\).md) 和 [DirectCast Operator](../Topic/DirectCast%20Operator%20\(Visual%20Basic\).md) 關鍵字會擲回執行階段例外狀況。[TryCast Operator](../Topic/TryCast%20Operator%20\(Visual%20Basic\).md) 關鍵字只適用於參考類型，並會在轉換失敗時傳回 [Nothing](../Topic/Nothing%20\(Visual%20Basic\).md)。  
  
3.  如果有縮小轉換，而且您的程式可以容許執行階段失敗，或您確定執行階段不可能失敗，您可以在原始程式碼開頭指定 `Option Strict Off`。 不過，您仍須將轉換置於 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md) 區塊中，以避免發生非預期的結果，或提早結束您的程式。  
  
4.  如果沒有從 `<type1>` 到 `<type2>` 的轉換，您必須重新評估程式邏輯。 您或許可以撰寫程式碼，將值指派給對應至 `<type1>` 之預期值的 `<type2>`。  
  
5.  如果沒有從 `<type1>` 到 `<type2>` 的轉換，而且其中一個類型是已定義的類別或結構，您或許可以定義轉換運算子，在該類型與其他類型之間進行轉換。 如需詳細資訊，請參閱[How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)。  
  
6.  一般來說，在所有情況下，除非您可以攔截 `Catch` 區塊中的失敗並有效地加以處理，否則您應該避免使用縮小轉換。  
  
## 請參閱  
 [Option Strict Statement](../Topic/Option%20Strict%20Statement.md)   
 [Widening and Narrowing Conversions](../Topic/Widening%20and%20Narrowing%20Conversions%20\(Visual%20Basic\).md)   
 [CType 函式](../Topic/CType%20Function%20\(Visual%20Basic\).md)   
 [DirectCast Operator](../Topic/DirectCast%20Operator%20\(Visual%20Basic\).md)   
 [TryCast Operator](../Topic/TryCast%20Operator%20\(Visual%20Basic\).md)   
 [Nothing](../Topic/Nothing%20\(Visual%20Basic\).md)   
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)