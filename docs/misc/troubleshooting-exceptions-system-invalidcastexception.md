---
title: "疑難排解例外狀況：System.InvalidCastException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "InvalidCastException 類別"
ms.assetid: a855dfe1-5c06-45a6-9c2f-c9e799ccf8f0
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.InvalidCastException
在明確參考轉換期間發生失敗時，就會擲回 <xref:System.InvalidCastException> 例外狀況。 所謂的參考轉換，就是從一種參考型別轉換為另一種參考型別。 雖然使用者可能會變更參考的型別，但不會變更轉換目標的類型或值。 將物件從某一型別轉型為另一種型別，是這個例外狀況最常發生的原因。  
  
## 相關秘訣  
 **請根據目的型別檢查來源型別，確定轉換是有效的。**  
 如需系統所支援轉換的詳細資訊，請參閱 <xref:System.Convert>。  
  
## 備註  
 若要使明確參考轉換成功，來源值必須是 Null \(在 Visual Basic 中為 `Nothing`\)，或是來源引數所參考的物件型別必須是隱含參考轉換所能轉換的目的型別。  
  
 當 Visual Basic 6.0 應用程式 \(具有在使用者控制項中的自訂事件呼叫\) 升級為新版的 Visual Basic 並開始執行時，便可能會發生這個例外狀況，其中的資訊為：「指定的轉換無效」。 若要解決這個錯誤，請找出  `Form1` 的下列程式碼行：  
  
 `Call UserControl11_MyCustomEvent(UserControl11, New UserControl1.MyCustomEventEventArgs(5))`  
  
 並使用下列程式碼取代：  
  
 `Call UserControl11_MyCustomEvent(UserControl11(0), New UserControl1.MyCustomEventEventArgs(5))`  
  
## 請參閱  
 <xref:System.InvalidCastException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [How to: Convert an Object to Another Type in Visual Basic](../Topic/How%20to:%20Convert%20an%20Object%20to%20Another%20Type%20in%20Visual%20Basic.md)   
 [將字串轉換成 .NET Framework 資料型別](../Topic/Converting%20Strings%20to%20.NET%20Framework%20Data%20Types.md)   
 [如何：在結構之間實作使用者定義的轉換](../Topic/How%20to:%20Implement%20User-Defined%20Conversions%20Between%20Structs%20\(C%23%20Programming%20Guide\).md)