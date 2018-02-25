---
title: "__writefsbyte、 __writefsdword、 __writefsqword、 __writefsword |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __writefsword
- __writefsbyte
- __writefsqword
- __writefsdword
dev_langs:
- C++
helpviewer_keywords:
- writefsbyte intrinsic
- __writefsword intrinsic
- writefsqword intrinsic
- writefsdword intrinsic
- __writefsdword intrinsic
- __writefsqword intrinsic
- __writefsbyte intrinsic
- writefsword intrinsic
ms.assetid: 23ac6e8e-bc91-4e90-a4c6-da02993637ad
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a469665569328e5df8cb107cf9e51590b9373da0
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="writefsbyte-writefsdword-writefsqword-writefsword"></a>__writefsbyte、__writefsdword、__writefsqword、__writefsword
**Microsoft 特定的**  
  
 寫入記憶體相對於 FS 區段的開頭位移所指定的位置。  
  
## <a name="syntax"></a>語法  
  
```  
void __writefsbyte(   
   unsigned long Offset,   
   unsigned char Data   
);  
void __writefsword(   
   unsigned long Offset,   
   unsigned short Data   
);  
void __writefsdword(   
   unsigned long Offset,   
   unsigned long Data   
);  
void __writefsqword(   
   unsigned long Offset,   
   unsigned __int64 Data   
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `Offset`  
 從寫入 FS 開頭的位移。  
  
 [輸入] `Data`  
 要寫入的值。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__writefsbyte`|x86|  
|`__writefsword`|x86|  
|`__writefsdword`|x86|  
|`__writefsqword`|x86|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 這些常式會只提供內建函式。  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [__readfsbyte, \__readfsdword, \__readfsqword, \__readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)