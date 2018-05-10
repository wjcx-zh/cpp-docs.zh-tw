---
title: HUGE_VAL、_HUGE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _HUGE
apilocation:
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _HUGE
- HUGE_VAL
dev_langs:
- C++
helpviewer_keywords:
- _HUGE constant
- HUGE_VAL constant
- double value
ms.assetid: 3f044b45-02cd-46b2-b1de-87fd0441dd6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2d763b8c5379223ddacb8077c463efa0b91acfa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="hugeval-huge"></a>HUGE_VAL、_HUGE
## <a name="syntax"></a>語法  
  
```  
  
#include <math.h>  
  
```  
  
## <a name="remarks"></a>備註  
 `HUGE_VAL` 是最大的可表示雙精度浮點數值。 發生錯誤時，許多執行階段數學函式會傳回這個值。 針對某些函式，會傳回 -`HUGE_VAL`。 `HUGE_VAL` 定義為 `_HUGE`，但執行階段數學函式傳回 `HUGE_VAL`。 為保持一致性，您也應該在程式碼中使用 `HUGE_VAL`。  
  
## <a name="see-also"></a>請參閱  
 [全域常數](../c-runtime-library/global-constants.md)