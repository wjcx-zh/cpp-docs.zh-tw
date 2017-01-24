---
title: "事件 &#39;&lt;事件名稱&gt;&#39; 的 &#39;&lt;程序名稱&gt;&#39; 方法無法標記為符合 CLS 標準，因為其包含類型 &#39;&lt;類型名稱&gt;&#39; 不符合 CLS 標準 | Microsoft Docs"
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
  - "vbc40053"
  - "bc40053"
helpviewer_keywords: 
  - "BC40053"
ms.assetid: 5f7aaf64-b5e6-4f97-9ebd-44cd4c7e8bf5
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 事件 &#39;&lt;事件名稱&gt;&#39; 的 &#39;&lt;程序名稱&gt;&#39; 方法無法標記為符合 CLS 標準，因為其包含類型 &#39;&lt;類型名稱&gt;&#39; 不符合 CLS 標準
自訂事件宣告 `AddHandler` 或 `RemoveHandler` 程序並將其標記為 `<CLSCompliant(True)>`，但事件已在標記為 `<CLSCompliant(False)>` 或未標記的類型中定義。  
  
 將 <xref:System.CLSCompliantAttribute> 套用至程式設計項目時，請將屬性的 `isCompliant` 參數設定為 `True` 或 `False`，表示符合標準或不符合標準。 這個參數沒有預設值，您必須提供值。  
  
 如果您未將 <xref:System.CLSCompliantAttribute> 套用至項目，則視為不符合標準。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC40053  
  
### 更正這個錯誤  
  
-   如果您必須符合 CLS 標準，請在符合 CLS 標準的類型中定義事件。  
  
-   如果您需要將事件保留在其包含類型中，請從其定義中移除 <xref:System.CLSCompliantAttribute> 或將其標記為 `<CLSCompliant(False)>`。  
  
## 請參閱  
 [How to: Declare Custom Events To Avoid Blocking](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Avoid%20Blocking%20\(Visual%20Basic\).md)   
 [How to: Declare Custom Events To Conserve Memory](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Conserve%20Memory%20\(Visual%20Basic\).md)   
 [不在組建中：AddHandler 和 RemoveHandler](http://msdn.microsoft.com/zh-tw/a7a24bd2-519a-46fe-8a2c-2b9df2ca28ef)   
 [\<PAVE OVER\> 撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/zh-tw/4c705105-69a2-4e5e-b24e-0633bc32c7f3)