---
title: "fenv_access |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
dev_langs: C++
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 623c9cb9af1d7df137aa7ee92071e34ad99a6331
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fenvaccess"></a>fenv_access
停用 (ON) 或啟用 (OFF) 可變更旗標測試和模式變更的最佳化。  
  
## <a name="syntax"></a>語法  
  
```  
#pragma fenv_access [ON | OFF]  
```  
  
## <a name="remarks"></a>備註  
 根據預設，`fenv_access` 為 OFF。  
  
 如需有關浮點數行為的詳細資訊，請參閱[/fp （指定浮點行為）](../build/reference/fp-specify-floating-point-behavior.md)。  
  
 受限於 `fenv_access` 的最佳化類型包括：  
  
-   全域通用子運算式刪除  
  
-   程式碼移動  
  
-   常數摺疊  
  
 其他浮點 pragma 包括：  
  
-   [float_control](../preprocessor/float-control.md)  
  
-   [fp_contract](../preprocessor/fp-contract.md)  
  
## <a name="example"></a>範例  
  
```  
// pragma_directive_fenv_access_x86.cpp  
// compile with: /O2  
// processor: x86  
#include <stdio.h>  
#include <float.h>   
#include <errno.h>  
#pragma fenv_access (on)  
  
int main() {  
   double z, b = 0.1, t = 0.1;  
   unsigned int currentControl;  
   errno_t err;  
  
   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);  
   if (err != 0) {  
      printf_s("The function _controlfp_s failed!\n");  
      return -1;  
   }  
   z = b * t;  
   printf_s ("out=%.15e\n",z);  
}  
```  
  
```Output  
out=9.999999776482582e-003  
```  
  
## <a name="example"></a>範例  
 下列範例是產生 Itanium 處理器輸出檔的編譯器。 **/fp： 精確**應以手動方式計算，以擴充精確度其中值大於 FLT_MAX (3.402823466 e + 38F) 可計算超過，且該總和將產生 1.0 的結果，保留中繼結果。 **/fp: strict**保留中繼結果以其原始精確度 （浮點），因此第一個加法會產生無限大，保留在運算式。  
  
```  
// pragma_directive_fenv_access_IPF.cpp  
// compile with: /O2 /fp:precise  
// processor: IPF  
// compiling with /fp:precise prints 1.0F  
// compile with /fp:strict to print infinity  
  
#include <stdio.h>  
float arr[5] = {3.402823465e+38F,   
               3.402823462e+38F,  
               3.402823464e+38F,  
               3.402823463e+38F,  
               1.0F};  
  
int main() {  
   float sum = 0;  
   sum = arr[0] + arr[1] - arr[2] - arr[3] + arr[4];  
   printf_s("%f\n", sum);  
}  
```  
  
```Output  
1.000000  
```  
  
## <a name="example"></a>範例  
 從先前的範例將 `#pragma fenv_access (on)` 標記為註解時請注意，輸出會有所不同，因為編譯器會進行編譯時期求值，而不會使用控制模式。  
  
```  
// pragma_directive_fenv_access_2.cpp  
// compile with: /O2  
#include <stdio.h>  
#include <float.h>   
  
int main() {  
   double z, b = 0.1, t = 0.1;  
   unsigned int currentControl;  
   errno_t err;  
  
   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);  
   if (err != 0) {  
      printf_s("The function _controlfp_s failed!\n");  
      return -1;  
   }  
   z = b * t;  
   printf_s ("out=%.15e\n",z);  
}  
```  
  
```Output  
out=1.000000000000000e-002  
```  
  
## <a name="see-also"></a>請參閱  
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)