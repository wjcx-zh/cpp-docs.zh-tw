---
title: "Dual Interfaces and Events | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "雙重介面, 事件"
  - "事件 [C++], 雙重介面"
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Dual Interfaces and Events
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當設計事件介面以雙重時，可能會有許多虛擬設計理由並未這樣做。  這個的主要原因是事件的來源只會引發事件會透過 vtable 或透過 `Invoke`，不能同時指定兩者。  如果事件來源引發事件做為直接 vtable 方法呼叫，永遠不會使用 `IDispatch` 方法，而是實際介面應為純 vtable 介面。  如果事件來源引發事件做為呼叫 `Invoke`，永遠不會使用 vtable 方法，而是實際介面應該是分配介面。  如果您定義了事件連接雙重，您需要用戶端實作永遠不會使用的介面。  
  
> [!NOTE]
>  這個引數不適用於雙重介面，一般而言。  從實作中，雙重是實作針對各種不同的用戶端可以存取的介面或資料，方便和支援的模式。  
  
 會進一步原因避免重複事件介面;Visual Basic 和 Internet Explorer 不支援這些項目。  
  
## 請參閱  
 [Dual Interfaces and ATL](../atl/dual-interfaces-and-atl.md)