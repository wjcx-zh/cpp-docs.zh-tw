---
title: "在其他資料表包含資料列參考時更新資料行 | Microsoft Docs"
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
  - "資料列集, 資料行更新"
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 在其他資料表包含資料列參考時更新資料行
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

某些提供者可以偵測資料列中有哪些資料行變更，但是大部分的提供者不具這個功能。  因此，當您嘗試更新的資料列具有參考時，更新該資料行可能就會產生錯誤。  若要解決這個問題，請建立另一個只包含要變更資料行的存取子。  將該存取子的編號傳遞給 `SetData`。  
  
## 請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)