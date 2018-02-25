---
title: "__readfsbyte、 __readfsdword、 __readfsqword、 __readfsword |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __readfsword
- __readfsdword
- __readfsbyte
- __readfsqword
dev_langs:
- C++
helpviewer_keywords:
- __readfsword intrinsic
- readfsword intrinsic
- __readfsdword intrinsic
- readfsbyte intrinsic
- __readfsbyte intrinsic
- readfsdword intrinsic
- readfsqword intrinsic
- __readfsqword intrinsic
ms.assetid: f6ee7203-4179-402c-a464-0746c84ce6ac
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8d7430e8ebdf86acb7db2d8605d63c4d94f18dd5
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="readfsbyte-readfsdword-readfsqword-readfsword"></a>__readfsbyte、__readfsdword、__readfsqword、__readfsword
**Microsoft 特定的**  
  
 讀取位置，相對於 FS 區段的開頭位移所指定的記憶體。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned char __readfsbyte(   
   unsigned long Offset   
);  
unsigned short __readfsword(   
   unsigned long Offset   
);  
unsigned long __readfsdword(   
   unsigned long Offset  
);  
unsigned __int64 __readfsqword(   
   unsigned long Offset   
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `Offset`  
 從開頭的位移`FS`來讀取。  
  
## <a name="return-value"></a>傳回值  
 記憶體的位元組、 word、 doubleword 或 quadword （如呼叫的函式名稱所指示） 的內容在位置`FS:[Offset]`。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__readfsbyte`|x86|  
|`__readfsdword`|x86|  
|`__readfsqword`|x86|  
|`__readfsword`|x86|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 這些常式會只提供內建函式。  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [__writefsbyte, \__writefsdword, \__writefsqword, \__writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)