---
title: __inword |Microsoft Docs
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
- __inword intrinsic
ms.assetid: 5c617edd-6709-40a1-aad2-40d5e39283c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5895f8e4efd56ddcc9ab16a91a6242db443f0821
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722913"
---
# <a name="inword"></a>__inword
**Microsoft 專屬**  
  
 使用指定的連接埠時，讀取資料`in`指令。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned short __inword(  
   unsigned short Port  
);  
```  
  
#### <a name="parameters"></a>參數  
*連接埠*<br/>
[in]要讀取的連接埠。  
  
## <a name="return-value"></a>傳回值  
 讀取資料的文字。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__inword`|x86、x64|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 此常式僅可作為內建常式使用。  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)