---
title: "_status87、_statusfp、_statusfp2 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _statusfp2
- _statusfp
- _status87
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
- _statusfp2
- _statusfp
- statusfp2
- _status87
- status87
- statusfp
dev_langs: C++
helpviewer_keywords:
- floating-point functions, getting status word
- floating-point numbers, status word
- status87 function
- status word, getting floating point
- statusfp function
- _statusfp function
- _statusfp2 function
- statusfp2 function
- _status87 function
- floating-point functions
- status word
ms.assetid: 7ef963fa-b1fb-429d-94d6-fbf282ab7432
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5ea17630a79d91dcc0d6f9ce7fa3bd797159f528
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="status87-statusfp-statusfp2"></a>_status87、_statusfp、_statusfp2
取得浮點狀態字組。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned int _status87( void );  
unsigned int _statusfp( void );  
void _statusfp2(unsigned int *px86, unsigned int *pSSE2)  
```  
  
#### <a name="parameters"></a>參數  
 `px86`  
 這個位址會填入 x87 浮點單位的狀態字組。  
  
 `pSSE2`  
 這個位址會填入 SSE2 浮點單位的狀態字組。  
  
## <a name="return-value"></a>傳回值  
 針對 `_status87` 和 `_statusfp`，所傳回值中的位元表示浮點狀態。 如需 `_statusfp` 所傳回位元的定義，請參閱 FLOAT.H 包含檔案。 許多數學程式庫函式都會修改浮點狀態字組，伴隨著無法預期的結果。 最佳化可以重新排列、合併和消除 `_status87`、`_statusfp` 和相關函式呼叫的浮點運算。 使用 [/Od (停用 (偵錯))](../../build/reference/od-disable-debug.md) 編譯器選項或 [fenv_access](../../preprocessor/fenv-access.md) pragma 指示詞，防止最佳化重新排序浮點運算。 如果在浮點狀態字組之已知狀態之間執行較少浮點運算，則來自 `_clearfp` 和 `_statusfp` 的傳回值以及 `_statusfp2` 的傳回參數更加可靠。  
  
## <a name="remarks"></a>備註  
 `_statusfp` 函式會取得浮點狀態字組。 狀態字組是浮點處理器狀態與浮點例外狀況處理常式所偵測到之其他條件的組合，例如浮點堆疊溢位和反向溢位。 傳回狀態字組的內容之前，會檢查取消遮罩的例外狀況。 這表示會通知呼叫端有關暫止例外狀況。 在 x86 平台上，`_statusfp` 會傳回 x87 與 SSE2 浮點狀態的組合。 在 x64 平台上，傳回的狀態是根據 SSE 的 MXCSR 狀態。 在 ARM 平台上，`_statusfp` 會傳回 FPSCR 暫存器中的狀態。  
  
 `_statusfp` 是 `_status87` 之與平台無關的可攜式版本。 其等同於 Intel (x86) 平台上的 `_status87`，也受 x64 和 ARM 平台支援。 若要確保您的浮點程式碼可移植到所有結構，請使用 `_statusfp`。 如果您僅以 x86 平台為目標，您可以使用 `_status87` 或 `_statusfp`。  
  
 建議針對同時具有 x87 和 SSE2 浮點處理器的晶片 (例如 Pentium IV) 使用 `_statusfp2`。 對於 `_statusfp2`，針對 x87 或 SSE2 浮點處理器使用浮點狀態字組來填入位址。 針對支援 x87 和 SSE2 浮點處理器的晶片，如果使用 `_statusfp` 或 `_controlfp`，而且動作因參照 x87 或 SSE2 浮點狀態字組而不明確，則 EM_AMBIGUOUS 會設為 1。 只有 x86 平台才支援 `_statusfp2` 函式。  
  
 這些函式不是適用於[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)因為 common language runtime (CLR) 只支援預設的浮點精確度。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_status87`, `_statusfp`, `_statusfp2`|\<float.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_statusfp.c  
// Build by using: cl /W4 /Ox /nologo crt_statusfp.c  
// This program creates various floating-point errors and  
// then uses _statusfp to display messages that indicate these problems.  
  
#include <stdio.h>  
#include <float.h>  
#pragma fenv_access(on)  
  
double test( void )  
{  
   double a = 1e-40;  
   float b;  
   double c;  
  
   printf("Status = 0x%.8x - clear\n", _statusfp());  
  
   // Assignment into b is inexact & underflows:   
   b = (float)(a + 1e-40);  
   printf("Status = 0x%.8x - inexact, underflow\n", _statusfp());  
  
   // c is denormal:   
   c = b / 2.0;   
   printf("Status = 0x%.8x - inexact, underflow, denormal\n",   
            _statusfp());  
  
   // Clear floating point status:   
   _clearfp();  
   return c;  
}  
  
int main(void)  
{  
   return (int)test();  
}  
```  
  
```Output  
Status = 0x00000000 - clear  
Status = 0x00000003 - inexact, underflow  
Status = 0x00080003 - inexact, underflow, denormal  
```  
  
## <a name="see-also"></a>另請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [_clear87、_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)   
 [_control87、_controlfp、\__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)