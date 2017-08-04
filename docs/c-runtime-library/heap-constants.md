---
title: "Heap 常數 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _HEAPBADPTR
- _HEAPEMPTY
- _HEAPBADBEGIN
- _HEAPOK
- _HEAPBADNODE
- _HEAPEND
dev_langs:
- C++
helpviewer_keywords:
- _HEAPOK constants
- _HEAPEND constants
- HEAPBADBEGIN constants
- _HEAPBADNODE constants
- HEAPBADNODE constants
- HEAPBADPTR constants
- _HEAPEMPTY constants
- HEAPEND constants
- HEAPOK constants
- HEAPEMPTY constants
- _HEAPBADBEGIN constants
- _HEAPBADPTR constants
- heap constants
ms.assetid: 3f751bb9-2dc4-486f-b5f5-9061c96d3754
caps.latest.revision: 6
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 378df280df8255b8a8e94656425da1b3c3468dd2
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="heap-constants"></a>堆積常數
## <a name="syntax"></a>語法  
  
```  
  
#include <malloc.h>  
  
```  
  
## <a name="remarks"></a>備註  
 這些常數會提供指示堆積狀態的傳回值。  
  
|常數|意義|  
|--------------|-------------|  
|`_HEAPBADBEGIN`|找不到初始標頭資訊，或標頭資訊不正確。|  
|`_HEAPBADNODE`|找到不正確的節點，或堆積已損毀。|  
|`_HEAPBADPTR`|**_HEAPINFO** 結構的 **_pentry** 欄位未包含堆積的有效指標 (僅限 `_heapwalk` 常式)。|  
|`_HEAPEMPTY`|堆積尚未初始化。|  
|`_HEAPEND`|已成功到達堆積的結尾 (僅限 `_heapwalk` 常式)。|  
|`_HEAPOK`|堆積一致 (僅限 `_heapset` 和 `_heapchk` 常式)。 目前為止沒有錯誤；**_HEAPINFO** 結構包含下一個項目的相關資訊 (僅限 `_heapwalk` 常式)。|  
  
## <a name="see-also"></a>另請參閱  
 [_heapchk](../c-runtime-library/reference/heapchk.md)   
 [_heapset](../c-runtime-library/heapset.md)   
 [_heapwalk](../c-runtime-library/reference/heapwalk.md)   
 [全域常數](../c-runtime-library/global-constants.md)
