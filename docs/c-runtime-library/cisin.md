---
title: _CIsin | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CIsin
apilocation:
- msvcr80.dll
- msvcr100.dll
- msvcrt.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr110_clr0400.dll
apitype: DLLExport
f1_keywords:
- CIsin
- _CIsin
dev_langs: C++
helpviewer_keywords:
- _CIsin intrinsic
- CIsin intrinsic
ms.assetid: f215f39a-2341-4f1c-ba8e-cb522451ceb2
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7e87589421c5a1e24c490a0f03928281bc7fb92b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cisin"></a>_CIsin
計算堆疊頂端值的正弦。  
  
## <a name="syntax"></a>語法  
  
```  
void __cdecl _CIsin();  
```  
  
## <a name="remarks"></a>備註  
 這個版本的 `sin` 函式具有編譯器了解的特定呼叫慣例。 因為它可以防止產生複本並協助暫存器配置，所以會加速執行。  
  
 產生的值會推入至堆疊的頂端。  
  
## <a name="requirements"></a>需求  
 **平台：**x86  
  
## <a name="see-also"></a>請參閱  
 [依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [sin、sinf、sinl、sinh、sinhf、sinhl](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)