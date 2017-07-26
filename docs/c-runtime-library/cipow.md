---
title: _CIpow | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CIpow
apilocation:
- msvcr100.dll
- msvcr110.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- CIpow
- _CIpow
dev_langs:
- C++
helpviewer_keywords:
- CIpow intrinsic
- _CIpow intrinsic
ms.assetid: 477aaf0c-ac58-4252-89dd-9f3e35d47536
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: c42e300f3c2a9480605f23e632f1b7046c7c8d88
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="cipow"></a>_CIpow
根據堆疊頂端值計算 *x* 的 *y* 次方。  
  
## <a name="syntax"></a>語法  
  
```  
void __cdecl _CIpow();  
```  
  
## <a name="remarks"></a>備註  
 這個版本的 `pow` 函式具有編譯器了解的特定呼叫慣例。 因為它可以防止產生複本並協助暫存器配置，所以會加速執行。  
  
 產生的值會推入至堆疊的頂端。  
  
## <a name="requirements"></a>需求  
 **平台：**x86  
  
## <a name="see-also"></a>另請參閱  
 [依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [pow、powf、powl](../c-runtime-library/reference/pow-powf-powl.md)
