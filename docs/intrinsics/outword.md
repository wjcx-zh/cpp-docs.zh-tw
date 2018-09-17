---
title: __outword |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __outword
dev_langs:
- C++
helpviewer_keywords:
- __outword intrinsic
- out instruction
ms.assetid: 995f8834-0f50-4b4f-a7a2-af0e7c371cda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd5abaccb4adc9e642458669535cff369d963cfd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712572"
---
# <a name="outword"></a>__outword
**Microsoft 專屬**  
  
 會產生`out`的指示，將 word`Data`出所指定的 I/O 連接埠`Port`。  
  
## <a name="syntax"></a>語法  
  
```  
void __outword(   
   unsigned short Port,   
   unsigned short Data   
);  
```  
  
#### <a name="parameters"></a>參數  
*連接埠*<br/>
[in]若要將資料傳送至連接埠。  
  
*Data*<br/>
[in]要傳送的資料。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__outword`|x86、x64|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 此常式僅可作為內建常式使用。  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)