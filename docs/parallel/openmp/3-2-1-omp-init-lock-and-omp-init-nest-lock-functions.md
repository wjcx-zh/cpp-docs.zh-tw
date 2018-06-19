---
title: 3.2.1 omp_init_lock 和 omp_init_nest_lock 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 098a2721-b16a-484f-bc83-4b8e281e382c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f14e182e6c981cd5de7a4cf92d8c285a4b49c66
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695794"
---
# <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 omp_init_lock 和 omp_init_nest_lock 函式
這些函式提供初始化鎖定的唯一方法。 每個函式會初始化參數相關聯的鎖定*鎖定*供後續呼叫中使用。 格式如下：  
  
```  
#include <omp.h>  
void omp_init_lock(omp_lock_t *lock);  
void omp_init_nest_lock(omp_nest_lock_t *lock);  
```  
  
 已解除鎖定的初始狀態 （也就是沒有執行緒擁有鎖定）。 可巢狀的鎖定，初始的巢狀計數為零。 它會呼叫這些常式已經初始化的鎖定變數的任何一個不相容。