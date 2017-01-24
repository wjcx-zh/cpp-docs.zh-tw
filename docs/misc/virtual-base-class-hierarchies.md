---
title: "虛擬基底類別階層 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "類別 [c + +] 虛擬基底類別"
  - "類別階層架構，虛擬基底類別"
  - "在衍生的類別，類別階層考量"
  - "虛擬基底類別階層中的虛擬函式"
  - "基底類別虛擬"
  - "虛擬基底類別階層"
  - "虛擬基底類別的階層"
ms.assetid: d24fda17-f829-48d6-84ec-8100f26bc5cf
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 虛擬基底類別階層
部分類別階層相當廣泛，但有許多共同項目。 共同程式碼會在基底類別中實作，而特定程式碼則在衍生類別中實作。  
  
 基底類別必須建立通訊協定，衍生類別才能透過該協定發揮最大功能。 這些通訊協定通常會使用虛擬函式實作。 有時候，基底類別會提供此類函式的預設實作。 類別階層 \(例如「導向非循環圖的範例」中的 `Document` 階層，請參閱[單一繼承](../cpp/single-inheritance.md)\) 中常用的兩個函式是 `Identify` 和 `WhereIs`。  
  
 在呼叫時，`Identify` 函式會根據文件類型傳回正確的識別：若為 `Book`，`doc->Identify()` 之類的函式呼叫必須傳回 ISBN 編號；但如果是 `HelpFile`，傳回產品名稱和修訂編號可能會比較適合。 同樣地，`WhereIs` 應該傳回 `Book` 的某一列或某個書架，而若是 `HelpFile`，則應傳回磁碟位置 \(可能是目錄和檔案名稱\)。  
  
 重要的是，`Identify` 和 `WhereIs` 函式的所有實作都會傳回相同類型的資訊。 在這個情況中，字元字串是合適的。  
  
 這些函式會實作為虛擬函式，然後使用基底類別指標叫用。 實際程式碼的繫結會發生於執行階段，並選取正確的 `Identify` 或 `WhereIs` 函式。  
  
## 請參閱  
 [衍生類別概觀](../misc/overview-of-derived-classes.md)