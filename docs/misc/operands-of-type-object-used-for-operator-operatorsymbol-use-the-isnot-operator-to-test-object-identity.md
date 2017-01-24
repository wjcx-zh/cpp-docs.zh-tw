---
title: "供運算子 &#39;&lt;運算子符號&gt;&#39; 使用的類型 Object 的運算元；請使用 &#39;IsNot&#39; 運算子測試物件識別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42032"
  - "bc42032"
helpviewer_keywords: 
  - "BC42032"
ms.assetid: f43b163b-f8f6-489d-ba9e-df6398ccc553
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 供運算子 &#39;&lt;運算子符號&gt;&#39; 使用的類型 Object 的運算元；請使用 &#39;IsNot&#39; 運算子測試物件識別
運算式會搭配使用 `<>` 運算子與 [Object Data Type](../Topic/Object%20Data%20Type.md)的一個或兩個運算元。  
  
 您應該使用 `Is` 或 `IsNot` 運算子，來判斷兩個物件參考是否參考相同的物件執行個體。 請參閱 [Comparison Operators in Visual Basic](../Topic/Comparison%20Operators%20in%20Visual%20Basic.md)中的＜比較物件＞。  
  
 變數或運算式評估為 `Object` 時，編譯器必須執行*「晚期繫結」*\(late binding\)，因而導致執行階段的額外作業。 它也可能會讓您的應用程式發生執行階段錯誤。 例如，如果您將 <xref:System.Windows.Forms.Form> 指派給 `Object` 變數，然後嘗試將它與 `<>` 運算子搭配使用，則執行階段會擲回 <xref:System.InvalidCastException>，因為 Visual Basic 無法將 <xref:System.Windows.Forms.Form> 物件轉換成適用於數值比較的資料類型。 即使兩個運算元都評估為類型 <xref:System.Windows.Forms.Form>，作業還是會失敗，因為未定義 <xref:System.Windows.Forms.Form> 運算元的 `<>`。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC42032  
  
### 更正這個錯誤  
  
-   如果您想要判斷兩個物件參考是否參考相同的物件執行個體，請使用 `Is` 或 `IsNot` 運算子。  
  
## 請參閱  
 [Comparison Operators in Visual Basic](../Topic/Comparison%20Operators%20in%20Visual%20Basic.md)   
 [IsNot Operator](../Topic/IsNot%20Operator%20\(Visual%20Basic\).md)   
 [How to: Determine Whether Two Objects Are Related](../Topic/How%20to:%20Determine%20Whether%20Two%20Objects%20Are%20Related%20\(Visual%20Basic\).md)   
 [How to: Determine Whether Two Objects Are Identical](../Topic/How%20to:%20Determine%20Whether%20Two%20Objects%20Are%20Identical%20\(Visual%20Basic\).md)