---
title: "A.31 安全執行緒的鎖定函式 |Microsoft 文件"
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
ms.assetid: 3ad89eb8-076c-405a-be5e-88d3d707a832
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 34a1d9b2a923af68bb63fb29a7031a7efa433a26
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="a31---thread-safe-lock-functions"></a>A.31 安全執行緒鎖定函式
下列 c + + 範例示範如何初始化在平行區域中的鎖定陣列使用`omp_init_lock`([區段 3.2.1](../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md) 42 頁面上)。  
  
## <a name="example"></a>範例  
  
### <a name="code"></a>程式碼  
  
```  
// A_13_omp_init_lock.cpp  
// compile with: /openmp  
#include <omp.h>  
  
omp_lock_t *new_locks() {  
   int i;  
   omp_lock_t *lock = new omp_lock_t[1000];  
   #pragma omp parallel for private(i)  
   for (i = 0 ; i < 1000 ; i++)  
      omp_init_lock(&lock[i]);  
  
   return lock;  
}  
  
int main () {}  
```