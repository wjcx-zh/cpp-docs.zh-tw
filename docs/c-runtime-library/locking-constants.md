---
title: "_locking 常數 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _LK_RLCK
- _LK_NBLCK
- _LK_LOCK
- _LK_NBRLCK
- _LK_UNLCK
dev_langs: C++
helpviewer_keywords:
- LK_UNLCK constant
- LK_NBRLCK constant
- _LK_NBRLCK constant
- _LK_NBLCK constant
- _LK_LOCK constant
- LK_NBLCK constant
- _LK_UNLCK constant
- LK_RLCK constant
- _LK_RLCK constant
- LK_LOCK constant
ms.assetid: c3dc92c8-60e3-4d29-9f50-5d217627c8ad
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 799b00209463c90c61b4b497a88af39ba554cd01
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="locking-constants"></a>_locking 常數
## <a name="syntax"></a>語法  
  
```  
  
#include <sys/locking.h>  
  
```  
  
## <a name="remarks"></a>備註  
 針對 `_locking` 函式呼叫中的 *mode* 引數中會指定要執行的鎖定動作。  
  
 *mode* 引數必須是下列其中一個資訊清單常數。  
  
 `_LK_LOCK`  
 鎖定指定的位元組。 如果無法鎖定位元組，函式會在 1 秒後重試。 如果嘗試 10 次之後還是無法鎖定位元組，函式會傳回錯誤。  
  
 `_LK_RLCK`  
 與 `_LK_LOCK` 相同。  
  
 `_LK_NBLCK`  
 鎖定指定的位元組。 如果無法鎖定位元組，函式會傳回錯誤。  
  
 `_LK_NBRLCK`  
 與 `_LK_NBLCK` 相同。  
  
 `_LK_UNLCK`  
 解除指定位元組的鎖定。 (位元組先前必須為已鎖定)。  
  
## <a name="see-also"></a>另請參閱  
 [_locking](../c-runtime-library/reference/locking.md)   
 [全域常數](../c-runtime-library/global-constants.md)