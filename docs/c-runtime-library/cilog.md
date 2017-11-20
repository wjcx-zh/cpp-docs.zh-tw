---
title: _CIlog | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CIlog
apilocation:
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _CIlog
- CIlog
dev_langs: C++
helpviewer_keywords:
- _CIlog intrinsic
- CIlog intrinsic
ms.assetid: 23503854-ddaa-4fe0-a4a3-7fbb3a43bdec
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1ba78f83dd288d03ab08fc1ce11fc8b219371704
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="cilog"></a>_CIlog
計算堆疊頂端值的自然對數。  
  
## <a name="syntax"></a>語法  
  
```  
void __cdecl _CIlog();  
```  
  
## <a name="remarks"></a>備註  
 這個版本的 `log` 函式具有編譯器了解的特定呼叫慣例。 因為它可以防止產生複本並協助暫存器配置，所以會加速執行。  
  
 產生的值會推入至堆疊的頂端。  
  
## <a name="requirements"></a>需求  
 **平台：**x86  
  
## <a name="see-also"></a>另請參閱  
 [依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [log、logf、log10、log10f](../c-runtime-library/reference/log-logf-log10-log10f.md)