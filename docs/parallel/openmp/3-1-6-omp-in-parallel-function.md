---
title: 3.1.6 omp_in_parallel 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: db6e3a63-2a0a-4b8e-8cc6-c6b49edca5fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 22b491695d2ae49336d7d8998af64e724f344d87
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="316-ompinparallel-function"></a>3.1.6 omp_in_parallel 函式
**Omp_in_parallel**函式會傳回非零值，如果呼叫以平行方式執行的平行區域的動態範圍內; 否則它會傳回 0。 格式如下：  
  
```  
#include <omp.h>  
int omp_in_parallel(void);  
```  
  
 此函式會傳回非零的值中以平行方式，包括巢狀的區域中已序列化區域執行呼叫時。