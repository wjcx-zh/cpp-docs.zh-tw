---
title: "_set_SSE2_enable | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_set_SSE2_enable"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-math-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_set_SSE2_enable"
  - "set_SSE2_enable"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_set_SSE2_enable 函式"
  - "Streaming SIMD Extensions 2 指示"
  - "set_SSE2_enable 函式"
ms.assetid: 55db895d-fc1e-475a-9110-b781a9bb51c5
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _set_SSE2_enable
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

啟用或停用使用 CRT 數學常式中的 [Streaming SIMD Extensions 2](http://msdn.microsoft.com/zh-tw/f98440eb-73a9-4f96-b203-ac41bb6701ea) \(SSE2\) 指令。\(因為預設上 SSE2 會是啟用的，這個函式在 x64 架構上是不可用的。\)  
  
## 語法  
  
```  
int _set_SSE2_enable(  
   int flag  
);  
```  
  
#### 參數  
 `flag`  
 1啟用 SSE2 實作；0則停用 SSE2 實作。  根據預設， SSE2 實作在支援它的處理器啟用。  
  
## 傳回值  
 如果SSE2 實作已啟用，則非零；如果SSE2 實作停用，則是零。  
  
## 備註  
 下列函式有可藉由使用`_set_SSE2_enable`來啟用SSE2的實作:  
  
-   [atan](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)  
  
-   [ceil](../../c-runtime-library/reference/ceil-ceilf-ceill.md)  
  
-   [exp](../../c-runtime-library/reference/exp-expf.md)  
  
-   [floor](../../c-runtime-library/reference/floor-floorf-floorl.md)  
  
-   [log](../../c-runtime-library/reference/log-logf-log10-log10f.md)  
  
-   [log10](../../c-runtime-library/reference/log-logf-log10-log10f.md)  
  
-   [modf](../../c-runtime-library/reference/modf-modff-modfl.md)  
  
-   [pow](../../c-runtime-library/reference/pow-powf-powl.md)  
  
 這些函式的資料實作比預設實作會提供一些不同的回應，因為 SSE2 中繼值是 64 位元浮點數量，但預設實作中的值是 80 位元浮點數量。  
  
> [!NOTE]
>  如果您使用 [\/Oi \(產生內建函式\)](../../build/reference/oi-generate-intrinsic-functions.md) 編譯器選項編譯專案，可能會使 `_set_SSE2_enable` 沒有作用。  `/Oi` 編譯器選項給編譯器權限使用內建取代 CRT 呼叫；這個行為覆寫 `_set_SSE2_enable`的作用。  如果您要確保 `/Oi` 不會覆寫 `_set_SSE2_enable`，請使用 `/Oi-` 來編譯專案。  當您使用隱含 `/Oi`的其他編譯器參數時，這也可能是很好的作法。  
  
 如果所有例外狀況有遮罩，則才可用SSE2 實作。  使用 [\_control87， \_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md) 已處理遮罩例外狀況。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_set_SSE2_enable`|\<math.h\>|  
  
 如需詳細資訊，請參閱介紹中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
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
  
 **Output**  
  
 `SSE2 enabled.`  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)