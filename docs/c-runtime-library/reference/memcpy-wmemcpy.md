---
title: memcpy、wmemcpy
ms.date: 11/04/2016
api_name:
- memcpy
- wmemcpy
api_location:
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wmemcpy
- memcpy
helpviewer_keywords:
- wmemcpy function
- memcpy function
ms.assetid: 34abb90b-bffb-46dc-a2f3-a5e9940839d6
ms.openlocfilehash: bf7f12cd00780347f23252764aace449dd6f5722
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303295"
---
# <a name="memcpy-wmemcpy"></a>memcpy、wmemcpy

複製緩衝區之間的位元組。 這些函式已有更安全的版本可用，請參閱 [memcpy_s、wmemcpy_s](memcpy-s-wmemcpy-s.md)。

## <a name="syntax"></a>語法

```C
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

### <a name="parameters"></a>參數

*dest*<br/>
新的緩衝區。

*src*<br/>
要複製的緩衝區。

*count*<br/>
要複製的字元數目。

## <a name="return-value"></a>傳回值

*Dest*的值。

## <a name="remarks"></a>備註

**memcpy**會將*計數*位元組從*src*複製到*目的地*;**wmemcpy**會複製整個*計數*的寬字元（兩個位元組）。 如果來源和目的地重迭， **memcpy**的行為會是未定義的。 使用**memmove**來處理重迭的區域。

> [!IMPORTANT]
> 確定目的地緩衝區與來源緩衝區是相同大小，或大於來源緩衝區。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/win32/SecBP/avoiding-buffer-overruns)。

> [!IMPORTANT]
> 因為有太多緩衝區溢位，因而導致潛在的安全性漏洞，所以已追蹤到不當的**memcpy**使用方式，所以安全性開發週期（SDL）會在「禁止」的功能中列出此功能。  您可能會發現有些 VC + + 程式庫類別會繼續使用**memcpy**。  此外，您可能會發現 VC + + 編譯器優化工具有時會發出對**memcpy**的呼叫。  Visual C++ 產品開發是依據 SDL 程序，因此已仔細評估過此禁用函式的使用方式。  程式庫使用它時，已仔細檢查過呼叫，以確定這些呼叫不會容許緩衝區滿溢。  在編譯器的情況下，有時會將某些程式碼模式辨識為與**memcpy**的模式相同，因此會以函式的呼叫取代。  在這種情況下，使用**memcpy**並不會比原本的指示更安全：它們只是為了呼叫效能微調的**memcpy**函數而優化。  就像使用「安全的」 CRT 函式並不保證安全性一樣（它們只是讓它變得不安全），使用「禁止」的函式並不保證危險（它們只需要更進一步的審查以確保安全性）。
>
> 由於 VC + + 編譯器和程式庫的**memcpy**使用已經仔細檢查過，因此在程式碼中允許這些呼叫與 SDL 相容。  應用程式原始程式碼中引進的**memcpy**呼叫，只有在安全性專家已審查過該使用方式時，才符合 SDL 的規範。

只有在包含語句之前定義常數 **_CRT_SECURE_DEPRECATE_MEMORY** ，才會取代**memcpy**和**wmemcpy**函數，以便讓函式被取代，例如下列範例中的：

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <memory.h>
```

或

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <wchar.h>
```

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**memcpy**|\<memory.h> 或 \<string.h>|
|**wmemcpy**|\<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

如需如何使用**memcpy**的範例，請參閱[memmove](memmove-wmemmove.md) 。

## <a name="see-also"></a>另請參閱

[緩衝區操作](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr、wmemchr](memchr-wmemchr.md)<br/>
[memcmp、wmemcmp](memcmp-wmemcmp.md)<br/>
[memmove、wmemmove](memmove-wmemmove.md)<br/>
[memset、wmemset](memset-wmemset.md)<br/>
[strcpy_s、wcscpy_s、_mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
[strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
