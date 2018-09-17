---
title: __outbyte |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __outbyte
dev_langs:
- C++
helpviewer_keywords:
- out instruction
- __outbyte intrinsic
ms.assetid: c4cd1a34-8a02-4e37-993d-3201bc17901a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cff8c2e8abfff713b4044ce58104c58b0a96da12
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719262"
---
# <a name="outbyte"></a>__outbyte
**Microsoft 專屬**  
  
 會產生`out`會傳送 1 個位元組所指定的指令`Data`出所指定的 I/O 連接埠`Port`。  
  
## <a name="syntax"></a>語法  
  
```  
void __outbyte(   
   unsigned short Port,   
   unsigned char Data   
);  
```  
  
#### <a name="parameters"></a>參數  
*連接埠*<br/>
[in]若要將資料傳送至連接埠。  
  
*Data*<br/>
[in]送出指定的連接埠位元組。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__outbyte`|x86、x64|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 此常式僅可作為內建常式使用。  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)