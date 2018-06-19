---
title: 3.2.4 omp_unset_lock 和 omp_unset_nest_lock 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5357e43e-a7c0-41d7-b529-3f7d15da8b11
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f480a75efff737356c1477593e182537ae73a8c8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690217"
---
# <a name="324-ompunsetlock-and-ompunsetnestlock-functions"></a>3.2.4 omp_unset_lock 和 omp_unset_nest_lock 函式
這些函式提供的方法釋放的鎖定擁有權。 格式如下：  
  
```  
#include <omp.h>  
void omp_unset_lock(omp_lock_t *lock);  
void omp_unset_nest_lock(omp_nest_lock_t *lock);  
```  
  
 所有這些函式的引數必須指向執行函式的執行緒所擁有的初始化的鎖定變數。 如果執行緒未擁有該鎖定，則行為是未定義。  
  
 簡單的鎖定，`omp_unset_lock`函式會釋放鎖定的擁有權從執行函式的執行緒。  
  
 可巢狀的鎖定，`omp_unset_nest_lock`函式會遞減的巢狀的計數和釋放鎖定的擁有權從執行函式，如果得出的計數為零的執行緒。