---
title: __outwordstring |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __outwordstring
dev_langs:
- C++
helpviewer_keywords:
- rep outsw instruction
- __outwordstring intrinsic
- outsw instruction
ms.assetid: b470c7a0-1de9-4370-886a-b2c3a1f842f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c49f76175ced83fb9a9b7e72e1c1fc7dbb68e20
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720664"
---
# <a name="outwordstring"></a>__outwordstring
**Microsoft 專屬**  
  
 會產生`rep outsw`指示，會傳送`Count`開頭的字`Buffer`出所指定的 I/O 連接埠`Port`。  
  
## <a name="syntax"></a>語法  
  
```  
void __outwordstring(   
   unsigned short Port,   
   unsigned short* Buffer,   
   unsigned long Count   
);  
```  
  
#### <a name="parameters"></a>參數  
*連接埠*<br/>
[in]若要將資料傳送至連接埠。  
  
*Buffer*<br/>
[in]指定的連接埠傳送資料的指標。  
  
*計數*<br/>
[in]要傳送的單字數目。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__outwordstring`|x86、x64|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 此常式僅可作為內建常式使用。  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)