---
title: "私用子句 A.21 範圍變數 |Microsoft 文件"
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
ms.assetid: 7cdb4a7f-af24-44ac-9d33-e43840bc8f3d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3d05a124e0b872210d28ed35fcd90872e0c051eb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="a21---scoping-variables-with-the-private-clause"></a>A.21 使用 private 子句設定變數範圍
值`i`和`j`在下列範例中並未定義在平行區域從結束：  
  
```  
int i, j;  
i = 1;  
j = 2;  
#pragma omp parallel private(i) firstprivate(j)  
{  
  i = 3;  
  j = j + 2;  
}  
printf_s("%d %d\n", i, j);  
```  
  
 如需有關`private`子句，請參閱[區段 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md)在 25 頁面上。