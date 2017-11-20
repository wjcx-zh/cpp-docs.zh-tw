---
title: "2.2 條件式編譯 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 8f9c914d-736c-48cf-899d-c8029dbe1e32
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ddfb754e3aa4142b6d070f2b5fe20ac7a63512e9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="22-conditional-compilation"></a>2.2 條件式編譯
_**OPENMP** OpenMP 相容的實作定義巨集名稱為十進位常數*yyyymm*，這將成為的年和月的已核准的規格。 這個巨集不能主旨**#define**或**#undef**前置處理器指示詞。  
  
```  
#ifdef _OPENMP  
iam = omp_get_thread_num() + index;  
#endif  
```  
  
 如果廠商定義的 OpenMP 擴充功能，它們可能會指定其他預先定義的巨集。