---
title: _set_SSE2_enable | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _set_SSE2_enable
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_SSE2_enable
- set_SSE2_enable
dev_langs:
- C++
helpviewer_keywords:
- _set_SSE2_enable function
- Streaming SIMD Extensions 2 instructions
- set_SSE2_enable function
ms.assetid: 55db895d-fc1e-475a-9110-b781a9bb51c5
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: d6db305c6674b974786cd6c17e6bf8b63b304aa2
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="setsse2enable"></a>_set_SSE2_enable
在 CRT 數學常式中啟用或停用 [Streaming SIMD Extensions 2](http://msdn.microsoft.com/en-us/f98440eb-73a9-4f96-b203-ac41bb6701ea) (SSE2) 指令的使用 (因為預設會啟用 SSE2，所以此函式不適用於 x64 結構)。  
  
## <a name="syntax"></a>語法  
  
```  
int _set_SSE2_enable(  
   int flag  
);  
```  
  
#### <a name="parameters"></a>參數  
 `flag`  
 1 啟用 SSE2 實作；0 停用 SSE2 實作。 根據預設，會在支援它的處理器上啟用 SSE2 實作。  
  
## <a name="return-value"></a>傳回值  
 如果啟用 SSE2 實作，則為非零；如果停用 SSE2 實作，則為零。  
  
## <a name="remarks"></a>備註  
 下列函式具有可使用 `_set_SSE2_enable` 所啟用的 SSE2 實作：  
  
-   [atan](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)  
  
-   [ceil](../../c-runtime-library/reference/ceil-ceilf-ceill.md)  
  
-   [exp](../../c-runtime-library/reference/exp-expf.md)  
  
-   [floor](../../c-runtime-library/reference/floor-floorf-floorl.md)  
  
-   [log](../../c-runtime-library/reference/log-logf-log10-log10f.md)  
  
-   [log10](../../c-runtime-library/reference/log-logf-log10-log10f.md)  
  
-   [modf](../../c-runtime-library/reference/modf-modff-modfl.md)  
  
-   [pow](../../c-runtime-library/reference/pow-powf-powl.md)  
  
 因為 SSE2 中間值是 64 位元浮點數量，但預設實作中間值是 80 位元浮點數量，所以這些函式的 SSE2 實作所提供的答案可能會與預設實作略有不同。  
  
> [!NOTE]
>  如果您使用 [/Oi (產生內建函式)](../../build/reference/oi-generate-intrinsic-functions.md) 編譯器選項來編譯專案，則可能會顯示 `_set_SSE2_enable` 沒有作用。 `/Oi` 編譯器選項可授權編譯器使用內建來取代 CRT 呼叫；這種行為會覆寫 `_set_SSE2_enable` 的效果。 如果您想要保證 `/Oi` 不覆寫 `_set_SSE2_enable`，請使用 `/Oi-` 來編譯專案。 當您使用表示 `/Oi` 的其他編譯器參數時，這也可能是不錯做法。  
  
 只有在遮罩所有例外狀況時，才會使用 SSE2 實作。 使用 [_control87、_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md) 來遮罩例外狀況。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_set_SSE2_enable`|\<math.h>|  
  
 如需相容性詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_set_SSE2_enable.c  
// processor: x86  
#include <math.h>  
#include <stdio.h>  
  
int main()  
{  
   int i = _set_SSE2_enable(1);  
  
   if (i)  
      printf("SSE2 enabled.\n");  
   else  
      printf("SSE2 not enabled; processor does not support SSE2.\n");  
}  
```  
  
 **輸出**  
  
 `SSE2 enabled.`  
  
## <a name="see-also"></a>另請參閱  
 [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)
