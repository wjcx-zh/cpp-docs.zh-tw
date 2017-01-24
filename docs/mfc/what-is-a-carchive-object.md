---
title: "什麼是 CArchive 物件 | Microsoft Docs"
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
  - "CArchive"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "封存物件 [C++]"
  - "封存 [C++], 用於序列化"
  - "緩衝, 可序列化的物件"
  - "緩衝區, 可序列化的物件"
  - "CArchive 類別, 關於 CArchive 類別"
ms.assetid: 843f1825-288d-4d89-a1fa-70e1f92d9b8b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 什麼是 CArchive 物件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CArchive` 物件為寫入提供型別安全緩衝機制或將 `CFile` 讀取的可序列化物件。  通常 `CFile` 物件代表磁碟檔案;不過，它也可能是記憶體檔案 \(`CSharedFile` 物件\)，或讓代表剪貼簿。  
  
 指定 `CArchive` 物件中 \(寫入\)，序列化資料或載入 \(讀取，序列化\) 資料，不過，絕對不會同時表示兩者。  `CArchive` 物件的存留期只限於一個傳遞至檔案的文字物件或讀取物件從檔案。  因此，需要兩個連續建立的 `CArchive` 物件序列化資料至檔案從檔案並將它還原序列化。  
  
 當封存儲存至檔案時的物件，保存附加 `CRuntimeClass` 的物件。  然後，，而另一個封存從檔案載入至記憶體， `CObject`衍生物件以動態方式重建根據物件的 `CRuntimeClass` 。  在寫入至檔案時的儲存的封存，指定物件可能已經參考多次。  載入封存，不過，一次只能將重建物件。  如需封存方式的詳細資訊附加 `CRuntimeClass` 資訊物件並重建物件，允許可能的多個參考，在 [Technical Note 2](../mfc/tn002-persistent-object-data-format.md)中說明。  
  
 當資料還原序列化到封存，封存累積資料，直到緩衝區已滿。  然後封存給 `CArchive` 物件的 `CFile` 物件寫入至它的緩衝區。  同樣地，，因為您讀取封存的資料，它會將資料從檔案到其緩衝區然後從緩衝區到您的序列化物件。  這個緩衝區減少硬碟完整讀取的次數，因而增進應用程式的效能。  
  
## 請參閱  
 [序列化：序列化物件](../mfc/serialization-serializing-an-object.md)