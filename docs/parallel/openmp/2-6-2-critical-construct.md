---
title: "2.6.2 critical Construct | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: c46ecd00-b4a2-4a5e-ba92-288c329e773a
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.6.2 critical Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**要徑**指示詞會識別一種建構，限定為單一執行緒的相關聯的結構化區塊的執行一次。  語法**要徑**指示詞時，如下所示：  
  
```  
#pragma omp critical [(name)]  new-line  
   structured-block  
```  
  
 選擇性*名稱*可能會用來識別關鍵區域。  用來識別關鍵區域的識別項有外部連結，並在標籤、 標籤、 成員和一般的識別項所使用的命名空間中分開的命名空間中。  
  
 執行緒等候的關鍵區域的開頭沒有其他執行緒正在執行 \(在程式中\) 具有相同名稱的關鍵區域。  所有未命名**要徑**指示詞將對應至同一個未指定的名稱。