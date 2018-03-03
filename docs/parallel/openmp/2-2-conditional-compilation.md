---
title: "2.2 條件式編譯 |Microsoft 文件"
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
ms.assetid: 8f9c914d-736c-48cf-899d-c8029dbe1e32
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1fb58458710c18f89f4057061b9c67b4eef1bbf0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="22-conditional-compilation"></a>2.2 條件式編譯
_**OPENMP** OpenMP 相容的實作定義巨集名稱為十進位常數*yyyymm*，這將成為的年和月的已核准的規格。 這個巨集不能主旨**#define**或**#undef**前置處理器指示詞。  
  
```  
#ifdef _OPENMP  
iam = omp_get_thread_num() + index;  
#endif  
```  
  
 如果廠商定義的 OpenMP 擴充功能，它們可能會指定其他預先定義的巨集。