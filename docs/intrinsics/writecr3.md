---
title: __writecr3 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _writecr3
dev_langs:
- C++
helpviewer_keywords:
- _writecr3 intrinsic
ms.assetid: 959d49fa-69d5-47cf-88d2-7688367fe38f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 10acb6af23dffef0a7067883ac5dbac5abd9234f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724233"
---
# <a name="writecr3"></a>__writecr3
**Microsoft 專屬**  
  
 將值寫入`Data`CR3 註冊。  
  
## <a name="syntax"></a>語法  
  
```  
void writecr3(   
   unsigned __int64 Data   
);  
```  
  
#### <a name="parameters"></a>參數  
*Data*<br/>
[in]要寫入的 CR3 暫存器的值。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__writecr3`|x86、x64|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 此內建只適用於核心模式，且此常式僅可作為內建常式使用。  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)