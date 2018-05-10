---
title: 3.2.3 omp_set_lock 和 omp_set_nest_lock 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b5323879-f72e-418e-953f-3979fdda17a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ba24e923051eb887db2a81c1d9765d31a4ef7b24
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="323-ompsetlock-and-ompsetnestlock-functions"></a>3.2.3 omp_set_lock 和 omp_set_nest_lock 函式
所有這些函式會封鎖執行函式，直到指定的鎖定可用，然後設定 鎖定的執行緒。 如果已解除鎖定使用簡單的鎖定。 如果已解除鎖定，或它已經由執行緒執行函式擁有使用可巢狀的鎖定。 格式如下：  
  
```  
#include <omp.h>  
void omp_set_lock(omp_lock_t *lock);  
void omp_set_nest_lock(omp_nest_lock_t *lock);  
```  
  
 簡單鎖定的引數`omp_set_lock`函式必須指向初始化的鎖定變數。 鎖定擁有權會授與執行函式的執行緒。  
  
 可巢狀的鎖定，以引數`omp_set_nest_lock`函式必須指向初始化的鎖定變數。 巢狀的計數會遞增，而執行緒授與，或會保留的鎖定擁有權。