---
title: "為變數 &#39;&lt;變數名稱&gt;&#39; 指派值之前，已用參考方式傳遞該變數 (結構變數) | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc42108"
  - "vbc42108"
helpviewer_keywords: 
  - "BC42108"
ms.assetid: 8f858dd7-db04-408e-ae67-e4ff2f0e5e30
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 為變數 &#39;&lt;變數名稱&gt;&#39; 指派值之前，已用參考方式傳遞該變數 (結構變數)
為變數 '\<變數名稱\>' 指派值之前，已用參考方式傳遞該變數。 在執行階段可能會產生 null 參考例外狀況。 確定結構或所有參考成員在使用前都已初始化  
  
 程序呼叫在為結構變數指派任何值之前，將變數當做引數傳遞至 `ByRef` 參數。  
  
 如果結構變數從未獲派值，則每個結構成員會保有其資料類型的預設值。 若是參考資料類型，該預設值為 [Nothing](../Topic/Nothing%20\(Visual%20Basic\).md)。 在某些情況下，讀取具有 `Nothing` 值的參考成員可能會導致 <xref:System.NullReferenceException>。  
  
 將引數傳遞至程序 `ByRef` 會將引數的基礎變數公開給程序進行可能的修改。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC42108  
  
### 更正這個錯誤  
  
-   如果不論結構成員是否已持有值，都想讓程序透過 `ByRef` 引數將值指派給成員，則不需要採取任何動作。  
  
-   如果程序中的邏輯在為結構成員指派任何值之前讀取成員，而且成員屬於實值類型，請確定程序邏輯並非取決於成員是否持有其預設值。  
  
-   如果程序中的邏輯在為結構成員指派任何值之前讀取成員，而且成員屬於參考類型，請確定程序邏輯可以處理 `Nothing` 值。 例如，它可以使用 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md) 來攔截 <xref:System.NullReferenceException>。  
  
## 請參閱  
 [Dim Statement](../Topic/Dim%20Statement%20\(Visual%20Basic\).md)   
 [Value Types and Reference Types](../Topic/Value%20Types%20and%20Reference%20Types.md)   
 [Passing Arguments by Value and by Reference](../Topic/Passing%20Arguments%20by%20Value%20and%20by%20Reference%20\(Visual%20Basic\).md)   
 [ByRef](../Topic/ByRef%20\(Visual%20Basic\).md)   
 [變數宣告](../Topic/Variable%20Declaration%20in%20Visual%20Basic.md)   
 [Structures](../Topic/Structures%20\(Visual%20Basic\).md)   
 [Structure Statement](../Topic/Structure%20Statement.md)   
 [為變數進行疑難排解](../Topic/Troubleshooting%20Variables%20in%20Visual%20Basic.md)