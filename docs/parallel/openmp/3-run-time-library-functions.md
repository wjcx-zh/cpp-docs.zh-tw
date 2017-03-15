---
title: "3.執行階段程式庫函式 | Microsoft Docs"
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
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.執行階段程式庫函式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本章節描述 OpenMP C 和 c + + 執行階段程式庫函式。 標頭 **\< omp.h >** 會宣告兩種類型，可用來控制和查詢的平行執行環境，並鎖定可以用於同步處理資料的存取權的函式的幾個函式。  
  
 型別 **omp_lock_t** 是物件型別能夠代表已鎖定可供使用，或執行緒擁有的鎖定。 這些鎖定會參照為 *簡單鎖定*。  
  
 型別 **omp_nest_lock_t** 是物件型別可以代表其中一個的鎖定，或者擁有鎖定的執行緒識別和 *巢狀計數* （如下所述）。 這些鎖定會參照為 *可巢狀鎖定*。  
  
 程式庫函式是使用 「 C 」 連結的外部函式。  
  
 在本章節描述可分成下列主題︰  
  
-   執行環境函式 (請參閱 [3.1 節](../../parallel/openmp/3-1-execution-environment-functions.md) 第 35 頁上)。  
  
-   鎖定函式 (請參閱 [第 3.2 節](../../parallel/openmp/3-2-lock-functions.md) 第 41 頁上)。