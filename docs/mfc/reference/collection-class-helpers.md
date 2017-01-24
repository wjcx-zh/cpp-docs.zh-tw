---
title: "集合類別 Helper | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.classes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "集合類別, Helper 函式"
  - "ConstructElements 函式"
  - "DestructElements 函式"
  - "Helper 函式集合類別"
  - "SerializeElements 函式"
ms.assetid: bc3a2368-9edd-4748-9e6a-13cba79517ca
caps.latest.revision: 14
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 集合類別 Helper
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

集合將 `CMap`、 `CList`和 `CArray` 全域使用樣板化 Helper 函式分類這類的用途與比較，複製和序列化項目。  做為依據 `CMap`的類別中實作時， `CList`和 `CArray`，必須視需要覆寫這些函式與版本適合在您的對應，清單或陣列儲存的資料型別。  如需覆寫 Helper 函式的資訊 \(例如 `SerializeElements`\)，請參閱本文件的 [集合:如何將型別安全集合](../../mfc/how-to-make-a-type-safe-collection.md)。  請注意 **ConstructElements** 和 **DestructElements** 都已被取代。  
  
 MFC 程式庫提供下列全域函式可幫助您自訂您的集合類別:  
  
### 集合類別 Helper  
  
|||  
|-|-|  
|[CompareElements](../Topic/CompareElements.md)|表示項目是否相同。|  
|[CopyElements](../Topic/CopyElements.md)|從陣列的元素複製到另一個。|  
|[DumpElements](../Topic/DumpElements.md)|提供的資料流導向診斷輸出。|  
|[HashKey](../Topic/HashKey.md)|計算雜湊機碼。|  
|[SerializeElements](../Topic/SerializeElements.md)|儲存或擷取項目從封存。|  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)   
 [CMap Class](../../mfc/reference/cmap-class.md)   
 [CList Class](../../mfc/reference/clist-class.md)   
 [CArray Class](../../mfc/reference/carray-class.md)