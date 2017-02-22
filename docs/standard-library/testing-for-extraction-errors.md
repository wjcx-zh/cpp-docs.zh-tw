---
title: "測試是否有擷取錯誤 | Microsoft Docs"
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
  - "擷取錯誤"
ms.assetid: 6a681028-adba-4557-8f7b-f137932905f8
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 測試是否有擷取錯誤
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

處理函式的輸出錯誤，討論 [處理函式的錯誤。](../standard-library/output-file-stream-member-functions.md)，套用至輸入資料流。  測試是否為錯誤在擷取時很重要。  考慮下列陳述式:  
  
```  
cin >> n;  
```  
  
 如果 `n` 是帶正負號的整數，大於 32,767 的值 \(允許的值或 MAX\_INT\) 設定資料流的 `fail` 位元和 `cin` 物件變成無法使用。  所有後續擷取產生立即傳回未儲存的值。  
  
## 請參閱  
 [輸入資料流](../standard-library/input-streams.md)