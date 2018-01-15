---
title: "3. 執行階段程式庫函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f1cbedf8782c9c5ccb25bda3f8b43df8a526f268
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="3-run-time-library-functions"></a>3.執行階段程式庫函式
本章節描述 OpenMP C 和 c + + 執行階段程式庫函式。 標頭 **\<omp.h >**會宣告兩種類型，可用來控制和查詢的平行執行環境，並鎖定函式，可用來同步處理資料的存取權的幾個函式。  
  
 型別**omp_lock_t**是可以代表的鎖定都可用的物件類型，或執行緒擁有鎖定。 這些鎖定會參照為*簡單鎖定*。  
  
 型別**omp_nest_lock_t**是物件類型可以代表任一的鎖定，或者擁有鎖定的執行緒識別和*巢狀計數*（如下所述）。 這些鎖定會參照為*可巢狀鎖定*。  
  
 程式庫函式是使用"C"連結的外部函式。  
  
 在本章節描述可分成下列主題：  
  
-   執行環境函式 (請參閱[3.1 節](../../parallel/openmp/3-1-execution-environment-functions.md)在 35 頁面上)。  
  
-   鎖定函式 (請參閱[第 3.2 節](../../parallel/openmp/3-2-lock-functions.md)41 頁面上)。