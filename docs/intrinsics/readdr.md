---
title: __readdr | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __readdr
dev_langs:
- C++
helpviewer_keywords:
- __readdr intrinsic
ms.assetid: 061b05da-c85e-4052-b392-106f14bb84f1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 99b40b8134832e9300bf9635a60cd3664f717793
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="readdr"></a>__readdr
讀取指定的偵錯暫存器的值。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned         __readdr(unsigned int DebugRegister);  
unsigned __int64 __readdr(unsigned int DebugRegister);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `DebugRegister`  
 從 0 到 7 可識別偵錯常數暫存器。  
  
## <a name="return-value"></a>傳回值  
 指定的偵錯暫存器的值。  
  
## <a name="remarks"></a>備註  
 這些內建函式只適用於核心模式，而常式只提供內建函式。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__readdr`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [__readeflags](../intrinsics/readeflags.md)