---
title: "緩衝區操作 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.memory
dev_langs:
- C++
helpviewer_keywords:
- buffers, manipulation routines
- buffers
ms.assetid: 164f4860-ce66-412c-8291-396fbd70f03e
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 5c9c6b61c03671da0bfe3b58456291ad642aa7ff
ms.lasthandoff: 03/30/2017

---
# <a name="buffer-manipulation"></a>緩衝區操作
您可以使用這些常式以位元組的基礎使用記憶體區域。  
  
### <a name="buffer-manipulation-routines"></a>緩衝區操作常式  
  
|常式|用法|  
|-------------|---------|  
|[_memccpy](../c-runtime-library/reference/memccpy.md)|從一個緩衝區複製字元到另一個緩衝區，直到已複製指定的字元或指定的字元數為止|  
|[memchr、wmemchr](../c-runtime-library/reference/memchr-wmemchr.md)|傳回緩衝區中在指定字元數內第一個出現之指定字元的指標|  
|[memcmp、wmemcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|比較兩個緩衝區的指定字元數|  
|[memcpy、wmemcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)、[memcpy_s、wmemcpy_s](../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)|將指定的字元數從一個緩衝區複製到另一個|  
|[_memicmp、_memicmp_l](../c-runtime-library/reference/memicmp-memicmp-l.md)|比較兩個緩衝區中指定數目的字元，而不考慮大小寫|  
|[memmove、wmemmove](../c-runtime-library/reference/memmove-wmemmove.md)、[memmove_s、wmemmove_s](../c-runtime-library/reference/memmove-s-wmemmove-s.md)|將指定的字元數從一個緩衝區複製到另一個|  
|[memset、wmemset](../c-runtime-library/reference/memset-wmemset.md)|使用指定字元初始化緩衝區中指定的位元組數目|  
|[_swab](../c-runtime-library/reference/swab.md)|交換資料位元組，並將它們儲存在指定的位置|  
  
 當來源和目標區域重疊時，只有 `memmove` 一定會正確複製完整的來源。  
  
## <a name="see-also"></a>另請參閱  
 [依類別區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)
