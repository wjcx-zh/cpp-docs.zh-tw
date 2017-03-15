---
title: "nonextensible Attribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "nonextensible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "雙重介面, nonextensible attribute"
  - "nonextensible attribute"
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# nonextensible Attribute
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果雙重介面無法擴充在執行階段 \(也就是您將不會傳遞 **IDispatch::Invoke** 提供透過 vtable 無法使用\) 的方法或屬性，您應該套用 **nonextensible** 屬性加入至介面定義。  這個屬性會提供資訊給可用來啟用完整程式碼驗證在編譯時期用戶端語言 \(例如 Visual Basic\)。  如果未提供這個屬性，在 Bug 直到執行階段的用戶端程式碼可能仍為隱藏。  
  
 如需 **nonextensible** 屬性的詳細資訊和範例，請參閱 [nonextensible](../windows/nonextensible.md)。  
  
## 請參閱  
 [Dual Interfaces and ATL](../atl/dual-interfaces-and-atl.md)