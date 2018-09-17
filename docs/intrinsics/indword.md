---
title: __indword |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __indword_cpp
- __indword
dev_langs:
- C++
helpviewer_keywords:
- in instruction
- __indword intrinsic
ms.assetid: 1068d686-586e-4e36-b962-d1d7c3315260
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c209036f6d606bfd25cf41e828eb6488a1d16036
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712526"
---
# <a name="indword"></a>__indword
**Microsoft 專屬**  
  
 從指定的連接埠使用讀取資料的一個雙精度浮點數字`in`指令。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned long __indword(  
   unsigned short Port  
);  
```  
  
#### <a name="parameters"></a>參數  
*連接埠*<br/>
[in]要讀取的連接埠。  
  
## <a name="return-value"></a>傳回值  
 從連接埠，讀取這個字。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__indword`|x86、x64|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 此常式僅可作為內建常式使用。  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)