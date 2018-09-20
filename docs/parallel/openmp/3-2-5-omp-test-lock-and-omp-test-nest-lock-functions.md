---
title: 3.2.5 omp_test_lock 和 omp_test_nest_lock 函式 |Microsoft Docs
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
ms.openlocfilehash: 5349134bf92f407d4b65df9b92e3eebe87c097c1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426142"
---
# <a name="325-omptestlock-and-omptestnestlock-functions"></a>3.2.5 omp_test_lock 和 omp_test_nest_lock 函式

這些函式會嘗試設定鎖定，但不是會封鎖執行緒的執行。 格式如下：

```
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

引數必須指向未初始化的鎖定的變數。 這些函式會嘗試在相同的方式來設定鎖定`omp_set_lock`和`omp_set_nest_lock`，不同之處在於它們不會封鎖執行緒的執行。

簡單的鎖定，`omp_test_lock`函式會傳回非零值，如果鎖定已成功設定; 否則它會傳回零。

可巢狀的鎖定，`omp_test_nest_lock`函式會傳回新的巢狀計數，如果鎖定已成功設定; 否則它會傳回零。