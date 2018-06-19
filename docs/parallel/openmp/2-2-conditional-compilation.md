---
title: 2.2 條件式編譯 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8f9c914d-736c-48cf-899d-c8029dbe1e32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3d8c7073548c015d9982b721387176a0ca658c2
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33685901"
---
# <a name="22-conditional-compilation"></a>2.2 條件式編譯
_**OPENMP** OpenMP 相容的實作定義巨集名稱為十進位常數*yyyymm*，這將成為的年和月的已核准的規格。 這個巨集不能主旨 **#define**或 **#undef**前置處理器指示詞。  
  
```  
#ifdef _OPENMP  
iam = omp_get_thread_num() + index;  
#endif  
```  
  
 如果廠商定義的 OpenMP 擴充功能，它們可能會指定其他預先定義的巨集。