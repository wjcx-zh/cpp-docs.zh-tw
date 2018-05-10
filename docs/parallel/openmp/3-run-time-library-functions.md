---
title: 3. 執行階段程式庫函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d747f775509c6b3b2b95be51d95ea937816d3cd1
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="3-run-time-library-functions"></a>3.執行階段程式庫函式
本章節描述 OpenMP C 和 c + + 執行階段程式庫函式。 標頭 **\<omp.h >** 會宣告兩種類型，可用來控制和查詢的平行執行環境，並鎖定函式，可用來同步處理資料的存取權的幾個函式。  
  
 型別**omp_lock_t**是可以代表的鎖定都可用的物件類型，或執行緒擁有鎖定。 這些鎖定會參照為*簡單鎖定*。  
  
 型別**omp_nest_lock_t**是物件類型可以代表任一的鎖定，或者擁有鎖定的執行緒識別和*巢狀計數*（如下所述）。 這些鎖定會參照為*可巢狀鎖定*。  
  
 程式庫函式是使用"C"連結的外部函式。  
  
 在本章節描述可分成下列主題：  
  
-   執行環境函式 (請參閱[3.1 節](../../parallel/openmp/3-1-execution-environment-functions.md)在 35 頁面上)。  
  
-   鎖定函式 (請參閱[第 3.2 節](../../parallel/openmp/3-2-lock-functions.md)41 頁面上)。