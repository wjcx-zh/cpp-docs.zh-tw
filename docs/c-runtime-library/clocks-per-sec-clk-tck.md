---
title: CLOCKS_PER_SEC、CLK_TCK | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- CLOCKS_PER_SEC
- CLK_TCK
dev_langs:
- C++
helpviewer_keywords:
- CLOCKS_PER_SEC
- CLK_TCK constant
ms.assetid: bc285106-383d-44cb-91bf-276ad7de57bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbcc64419a34ff763f3e116474687fbadf055f42
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="clockspersec-clktck"></a>CLOCKS_PER_SEC、CLK_TCK
## <a name="syntax"></a>語法  
  
```  
  
#include <time.h>  
```  
  
## <a name="remarks"></a>備註  
 以秒為單位的時間，是由 `clock` 函式所傳回並除以 `CLOCKS_PER_SEC` 的值。 `CLK_TCK` 和它相等，但已被視為過時。  
  
## <a name="see-also"></a>請參閱  
 [clock](../c-runtime-library/reference/clock.md)   
 [全域常數](../c-runtime-library/global-constants.md)