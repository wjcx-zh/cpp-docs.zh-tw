---
title: 3.2.5 omp_test_lock 和 omp_test_nest_lock 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 36818945-c22c-4c24-b754-4e73eba6f3f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5023f0b089d76e92be886f4917905f57dda7a018
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686223"
---
# <a name="325-omptestlock-and-omptestnestlock-functions"></a>3.2.5 omp_test_lock 和 omp_test_nest_lock 函式
這些函式會嘗試設定鎖定，但不是會封鎖執行緒的執行。 格式如下：  
  
```  
#include <omp.h>  
int omp_test_lock(omp_lock_t *lock);  
int omp_test_nest_lock(omp_nest_lock_t *lock);  
```  
  
 引數必須指向初始化的鎖定變數。 這些函式會嘗試以相同方式設定鎖定`omp_set_lock`和`omp_set_nest_lock`，但不會封鎖執行緒的執行。  
  
 簡單的鎖定，`omp_test_lock`函式會傳回非零值，如果已成功設定鎖定; 否則它會傳回零。  
  
 可巢狀的鎖定，`omp_test_nest_lock`函式會傳回新的巢狀計數，如果已成功設定鎖定; 否則它會傳回零。