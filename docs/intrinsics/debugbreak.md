---
title: __debugbreak |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __debugbreak_cpp
- __debugbreak
dev_langs:
- C++
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a3dcead3129c87b2d02f8822019af763c0fe8b8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="debugbreak"></a>__debugbreak
**Microsoft 特定的**  
  
 在您的程式碼中導致中斷點，在該位置，系統會提示使用者執行偵錯工具。  
  
## <a name="syntax"></a>語法  
  
```  
void __debugbreak();  
```  
  
## <a name="requirements"></a>需求  
  
|內建|架構|頁首|  
|---------------|------------------|------------|  
|`__debugbreak`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h>|  
  
## <a name="remarks"></a>備註  
 `__debugbreak`編譯器內建函式，類似於[DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297.aspx)，是可導致中斷點的可移植 Win32 方法。  
  
> [!NOTE]
>  編譯時 **/clr**，函式包含`__debugbreak`會編譯為 MSIL。 `asm int 3` 會導致函式編譯為原生。 如需詳細資訊，請參閱[__asm](../assembler/inline/asm.md)。  
  
 例如:   
  
```  
main() {  
   __debugbreak();  
}  
```  
  
 類似於：  
  
```  
main() {  
   __asm {  
      int 3  
   }  
}  
```  
  
 (在 x86 電腦上)。  
  
 此常式僅可作為內建常式使用。  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [關鍵字](../cpp/keywords-cpp.md)