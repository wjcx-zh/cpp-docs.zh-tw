---
title: __readpmc |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readpmc
dev_langs:
- C++
helpviewer_keywords:
- Read Performance Monitoring Counters instruction
- __readpmc intrinsic
- rdpmc instruction
ms.assetid: 14ed45a6-28b6-4635-8437-a597c04b43d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0a5a172a7b0f8a309f1d8fd0762e098dc5d416a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720027"
---
# <a name="readpmc"></a>__readpmc
**Microsoft 專屬**  
  
 會產生`rdpmc`指令，讀取效能監視所指定的計數器`counter`。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned __int64 __readpmc(   
   unsigned long counter   
);  
```  
  
#### <a name="parameters"></a>參數  
*counter*<br/>
[in]要讀取的效能計數器。  
  
## <a name="return-value"></a>傳回值  
 指定的效能計數器的值。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__readpmc`|x86、x64|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 此內建只適用於核心模式，且此常式僅可作為內建。  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)