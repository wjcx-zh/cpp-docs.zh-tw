---
title: __inbytestring |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __inbytestring
- __inbytestring_cpp
dev_langs:
- C++
helpviewer_keywords:
- rep insb instruction
- __inbytestring intrinsic
ms.assetid: fe549556-e7a3-4af3-8ebf-8a7dc3cb233b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7569c7034184adecf6bb452d7c406a762af4e20b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711655"
---
# <a name="inbytestring"></a>__inbytestring
**Microsoft 專屬**  
  
 使用指定的連接埠時，讀取資料`rep insb`指令。  
  
## <a name="syntax"></a>語法  
  
```  
void __inbytestring(  
   unsigned short Port,  
   unsigned char* Buffer,  
   unsigned long Count  
);  
```  
  
#### <a name="parameters"></a>參數  
*連接埠*<br/>
[in]要讀取的連接埠。  
  
*Buffer*<br/>
[out]從連接埠讀取的資料會寫入此處。  
  
*計數*<br/>
[in]要讀取之資料的位元組數目。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__inbytestring`|x86、x64|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 此常式僅可作為內建常式使用。  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)