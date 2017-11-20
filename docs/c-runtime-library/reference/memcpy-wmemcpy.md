---
title: "memcpy、wmemcpy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- memcpy
- wmemcpy
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
apitype: DLLExport
f1_keywords:
- wmemcpy
- memcpy
dev_langs: C++
helpviewer_keywords:
- wmemcpy function
- memcpy function
ms.assetid: 34abb90b-bffb-46dc-a2f3-a5e9940839d6
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 38c00e7d7c5eb9f4a1076ae3814c17a8062fe322
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="memcpy-wmemcpy"></a>memcpy、wmemcpy
複製緩衝區之間的位元組。 這些函式已有更安全的版本可用，請參閱 [memcpy_s、wmemcpy_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
void *memcpy(  
   void *dest,  
   const void *src,  
   size_t count   
);  
wchar_t *wmemcpy(  
   wchar_t *dest,  
   const wchar_t *src,  
   size_t count  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dest`  
 新的緩衝區。  
  
 `src`  
 要複製的緩衝區。  
  
 `count`  
 要複製的字元數目。  
  
## <a name="return-value"></a>傳回值  
 `dest` 的值。  
  
## <a name="remarks"></a>備註  
 `memcpy` 會將 `count` 位元組從 `src` 複製至 `dest`；`wmemcpy` 會複製 `count` 個寬字元 (兩個位元組)。 如果來源和目的地重疊，則 `memcpy` 的行為是未定義。 使用 `memmove` 處理重疊的區域。  
  
> [!IMPORTANT]
>  確定目的地緩衝區與來源緩衝區是相同大小，或大於來源緩衝區。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
> [!IMPORTANT]
>  因為這麼多緩衝區滿溢，因此有潛在的安全性入侵，進而追蹤到 `memcpy` 的不當使用，此函式由安全性開發週期 (SDL) 列在「禁止」的函式之列。  您可能會注意到一些 VC++ 程式庫類別仍繼續使用 `memcpy`。  此外，您可能會注意到 VC++ 編譯器最佳化工具有時候會發出 `memcpy` 呼叫。  Visual C++ 產品開發是依據 SDL 程序，因此已仔細評估過此禁用函式的使用方式。  程式庫使用它時，已仔細檢查過呼叫，以確定這些呼叫不會容許緩衝區滿溢。  若在編譯器中，有時特定程式碼模式會被辨識為與 `memcpy` 的模式相同，因此被函式的呼叫取代。  在這種情況下，使用 `memcpy` 不比原本的指令更安全；它們只是經過最佳化的效能微調 `memcpy` 函式的呼叫。  就像使用「安全的」CRT 函式並不保證安全性一樣 (只是使其較少有不安全的情況發生)，使用「禁止的」函式並不一定危險 (只是需要更嚴謹的監督以確保安全性)。  
>   
>  因為 VC++ 編譯器和程式庫的 `memcpy` 使用方式已經過謹慎仔細的檢查，所以程式碼中會允許這些呼叫，否則會不符合 SDL。  應用程式的原始程式碼中導入的 `memcpy` 呼叫，只有在經過安全性專家檢閱後，才符合 SDL。  
  
 如果為了使函式被取代，在包含的陳述式之前就已定義常數 `memcpy`，則 `wmemcpy` 和 `_CRT_SECURE_DEPRECATE_MEMORY` 函式就只能被取代，如下列範例所示：  
  
```  
#define _CRT_SECURE_DEPRECATE_MEMORY  
#include <memory.h>  
```  
  
 或  
  
```  
#define _CRT_SECURE_DEPRECATE_MEMORY  
#include <wchar.h>  
```  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`memcpy`|\<memory.h> 或 \<string.h>|  
|`wmemcpy`|\<wchar.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 如需如何使用 `memcpy` 的範例，請參閱 [memmove](../../c-runtime-library/reference/memmove-wmemmove.md)。  
  
## <a name="see-also"></a>另請參閱  
 [緩衝區操作](../../c-runtime-library/buffer-manipulation.md)   
 [_memccpy](../../c-runtime-library/reference/memccpy.md)   
 [memchr、wmemchr](../../c-runtime-library/reference/memchr-wmemchr.md)   
 [memcmp、wmemcmp](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [memmove、wmemmove](../../c-runtime-library/reference/memmove-wmemmove.md)   
 [memset、wmemset](../../c-runtime-library/reference/memset-wmemset.md)   
 [strcpy_s、wcscpy_s、_mbscpy_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)   
 [strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)