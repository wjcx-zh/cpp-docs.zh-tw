---
title: __writeeflags |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __writeeflags
dev_langs:
- C++
helpviewer_keywords:
- __writeeflags intrinsics
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a2885f2ea103ad43535b11c526b96ed42de45fd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340524"
---
# <a name="writeeflags"></a>__writeeflags
指定的值寫入程式狀態和控制 (EFLAGS) 註冊。  
  
## <a name="syntax"></a>語法  
  
```  
void __writeeflags(unsigned Value);  
void __writeeflags(unsigned __int64 Value);  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `Value`|要寫入至 EFLAGS 暫存器值。 `Value`參數為 32 位元長度為 32 位元平台和 64 位元長度為 64 位元平台。|  
  
## <a name="remarks"></a>備註  
 這些常式會只提供內建函式。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__writeeflags`|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [__readeflags](../intrinsics/readeflags.md)