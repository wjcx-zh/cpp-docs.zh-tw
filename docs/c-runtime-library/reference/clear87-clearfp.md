---
title: "_clear87、_clearfp | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _clearfp
- _clear87
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- clearfp
- _clearfp
- _clear87
- clear87
dev_langs:
- C++
helpviewer_keywords:
- clearing floating point status word
- clearfp function
- _clear87 function
- _clearfp function
- clear87 function
ms.assetid: 72d24a70-7688-4793-ae09-c96d33fcca52
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 4d7a7b05896bac9e1b3f4ac29ee24a6ad7d61a82
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="clear87-clearfp"></a>_clear87、_clearfp
取得及清除浮點狀態字組。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned int _clear87( void );  
unsigned int _clearfp( void );  
```  
  
## <a name="return-value"></a>傳回值  
 傳回值中的位元表示在呼叫 `_clear87` 或 `_clearfp` 之前的浮點狀態。 如需 `_clear87` 所傳回位元的完整定義，請參閱 Float.h。 許多數學程式庫函式會修改 8087/80287 狀態字組，伴隨著無法預期的結果。 來自 `_clear87` 和 `_status87` 的傳回值更加可靠，因為較少浮點作業在浮點狀態字組之已知狀態之間執行。  
  
## <a name="remarks"></a>備註  
 `_clear87` 函式會清除浮點狀態字組中的例外狀況旗標，將忙碌的位元設為 0，然後傳回狀態字組。 浮點狀態字組是 8087/80287 狀態字組和 8087/80287 例外狀況處理常式所偵測到其他條件的組合，例如浮點的堆疊溢位和反向溢位。  
  
 `_clearfp` 是 `_clear87` 常式之與平台無關的可攜式版本。 其等同於 Intel (x86) 平台上的 `_clear87`，也受 x64 和 ARM 平台支援。 若要確保您的浮點程式碼可移植到 x64 和 ARM，請使用 `_clearfp`。 如果您僅以 x86 平台為目標，您可以使用 `_clear87` 或 `_clearfp`。  
  
 這些函式已被取代，以編譯時[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)因為 common language runtime 只支援預設的浮點精確度。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_clear87`|\<float.h>|  
|`_clearfp`|\<float.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_clear87.c  
// compile with: /Od  
  
// This program creates various floating-point   
// problems, then uses _clear87 to report on these problems.  
// Compile this program with Optimizations disabled (/Od).   
// Otherwise the optimizer will remove the code associated with   
// the unused floating-point values.  
//  
  
#include <stdio.h>  
#include <float.h>  
  
int main( void )  
{  
   double a = 1e-40, b;  
   float x, y;  
  
   printf( "Status: %.4x - clear\n", _clear87()  );  
  
   // Store into y is inexact and underflows:  
   y = a;  
   printf( "Status: %.4x - inexact, underflow\n", _clear87() );  
  
   // y is denormal:   
   b = y;  
   printf( "Status: %.4x - denormal\n", _clear87() );  
}  
```  
  
```Output  
Status: 0000 - clear  
Status: 0003 - inexact, underflow  
Status: 80000 - denormal  
```  
  
## <a name="see-also"></a>另請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [_control87、_controlfp、\__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)   
 [_status87、_statusfp、_statusfp2](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)
