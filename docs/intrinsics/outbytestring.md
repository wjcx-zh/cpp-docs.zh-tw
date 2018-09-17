---
title: __outbytestring |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __outbytestring
dev_langs:
- C++
helpviewer_keywords:
- rep outsb instruction
- __outbytestring intrinsic
- outsb instruction
ms.assetid: c9150661-9c18-427f-bae8-710bba6ed78c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 54a816bd4df165b3df9de723560192ac9072b29c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718831"
---
# <a name="outbytestring"></a>__outbytestring
**Microsoft 專屬**  
  
 會產生`rep outsb`指示，將傳送第一個`Count`所指向的資料位元組`Buffer`所指定的連接埠`Port`。  
  
## <a name="syntax"></a>語法  
  
```  
void __outbytestring(   
   unsigned short Port,   
   unsigned char* Buffer,   
   unsigned long Count   
);  
```  
  
#### <a name="parameters"></a>參數  
*連接埠*<br/>
[in]若要將資料傳送至連接埠。  
  
*Buffer*<br/>
[in]指定的連接埠傳送資料。  
  
*計數*<br/>
[in]資料要傳送的位元組數目。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__outbytestring`|x86、x64|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 此常式僅可作為內建常式使用。  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)