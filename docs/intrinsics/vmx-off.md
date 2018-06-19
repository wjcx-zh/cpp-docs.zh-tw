---
title: __vmx_off | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_off
dev_langs:
- C++
helpviewer_keywords:
- VMXOFF instruction
- __vmx_off intrinsic
ms.assetid: 78a32d46-9291-406c-b982-a550855aff18
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82d94d1cd08d08a57cedf3709d18a46639e56925
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335402"
---
# <a name="vmxoff"></a>__vmx_off
**Microsoft 特定的**  
  
 停用虛擬機器擴充功能 (VMX) 操作處理器中。  
  
## <a name="syntax"></a>語法  
  
```  
void __vmx_off();  
```  
  
## <a name="remarks"></a>備註  
 `__vmx_off`函數即相當於`VMXOFF`機器指令。 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，搜尋文件，而 < Intel 虛擬化技術規格的 ia-32 Intel 架構 >、 文件編號 C97063-002，位於[Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127)站台。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__vmx_off`|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)