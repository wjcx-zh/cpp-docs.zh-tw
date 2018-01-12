---
title: "__debugbreak |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __debugbreak_cpp
- __debugbreak
dev_langs: C++
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 07cac11754a8b5f242c38d5fd45d4c7f0707d69a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
|`__debugbreak`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h >|  
  
## <a name="remarks"></a>備註  
 `__debugbreak`編譯器內建函式，類似於[DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297.aspx)，是可導致中斷點的可移植 Win32 方法。  
  
> [!NOTE]
>  編譯時**/clr**，函式包含`__debugbreak`會編譯為 MSIL。 `asm int 3` 會導致函式編譯為原生。 如需詳細資訊，請參閱[__asm](../assembler/inline/asm.md)。  
  
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
  
## <a name="see-also"></a>請參閱  
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [關鍵字](../cpp/keywords-cpp.md)