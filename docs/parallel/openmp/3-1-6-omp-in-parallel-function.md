---
title: "3.1.6 omp_in_parallel 函式 |Microsoft 文件"
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
ms.assetid: db6e3a63-2a0a-4b8e-8cc6-c6b49edca5fb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2e5d05af81eb112894ca27a7599c271138893ee1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="316-ompinparallel-function"></a>3.1.6 omp_in_parallel 函式
**Omp_in_parallel**函式會傳回非零值，如果呼叫以平行方式執行的平行區域的動態範圍內; 否則它會傳回 0。 格式如下：  
  
```  
#include <omp.h>  
int omp_in_parallel(void);  
```  
  
 此函式會傳回非零的值中以平行方式，包括巢狀的區域中已序列化區域執行呼叫時。