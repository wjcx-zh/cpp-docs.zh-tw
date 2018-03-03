---
title: "3.2.5 omp_test_lock 和 omp_test_nest_lock 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 36818945-c22c-4c24-b754-4e73eba6f3f8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8fcdacdbb38a9bb27e35ada74aa2139be10c6797
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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