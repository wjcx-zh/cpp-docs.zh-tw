---
title: "3.2.5 omp_test_lock 和 omp_test_nest_lock 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 36818945-c22c-4c24-b754-4e73eba6f3f8
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fa340ce56d0e669a40b131a4cb3efbe18fc3c430
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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