---
title: _CIsqrt | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CIsqrt
apilocation:
- msvcr90.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcrt.dll
- msvcr110.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _CIsqrt
- CIsqrt
dev_langs: C++
helpviewer_keywords:
- CIsqrt intrinsic
- _CIsqrt intrinsic
ms.assetid: 663548ea-398c-48ee-8397-a787c6ebb937
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5662683c53323d103105f04e872e91e137dbfe26
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cisqrt"></a>_CIsqrt
計算堆疊頂端值的平方根。  
  
## <a name="syntax"></a>語法  
  
```  
void __cdecl _CIsqrt();  
```  
  
## <a name="remarks"></a>備註  
 這個版本的 `sqrt` 函式具有編譯器了解的特定呼叫慣例。 因為它可以防止產生複本並協助暫存器配置，所以會加速執行。  
  
 產生的值會推入至堆疊的頂端。  
  
## <a name="requirements"></a>需求  
 **平台：**x86  
  
## <a name="see-also"></a>請參閱  
 [依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [sqrt、sqrtf、sqrtl](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)