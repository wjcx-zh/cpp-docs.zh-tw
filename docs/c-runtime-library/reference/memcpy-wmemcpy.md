---
title: memcpy、wmemcpy
ms.date: 11/04/2016
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
helpviewer_keywords:
- wmemcpy function
- memcpy function
ms.assetid: 34abb90b-bffb-46dc-a2f3-a5e9940839d6
ms.openlocfilehash: 0c71bd7b1a661a0964576e831e008d23692d4c2e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611181"
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

值*dest*。

## <a name="remarks"></a>備註

**memcpy**複本*計數*位元組*src*來*dest*;**wmemcpy**複本*計數*寬字元 （兩個位元組為單位）。 如果來源和目的地重疊，行為**memcpy**是未定義。 使用**memmove**處理重疊的區域。

> [!IMPORTANT]
> 確定目的地緩衝區與來源緩衝區是相同大小，或大於來源緩衝區。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/desktop/SecBP/avoiding-buffer-overruns)。

> [!IMPORTANT]
> 因為這麼多緩衝區滿溢，並因此有潛在的安全性弱點，進而追蹤到不當的使用方式**memcpy**，此函式會列在 「 禁止 」 函式的安全性開發生命週期 (SDL)。  您可能會注意到一些 VC + + 程式庫類別仍繼續使用**memcpy**。  此外，您可能會注意到 VC + + 編譯器最佳化工具有時會呼叫**memcpy**。  Visual C++ 產品開發是依據 SDL 程序，因此已仔細評估過此禁用函式的使用方式。  程式庫使用它時，已仔細檢查過呼叫，以確定這些呼叫不會容許緩衝區滿溢。  若在編譯器中，有時特定程式碼模式會被辨識為相同的模式**memcpy**，並因此會以函式的呼叫取代。  在此情況下，使用**memcpy**不再不安全，比原始指令; 它們只是已經過最佳化，呼叫的效能微調**memcpy**函式。  就像使用「安全的」CRT 函式並不保證安全性一樣 (只是使其較少有不安全的情況發生)，使用「禁止的」函式並不一定危險 (只是需要更嚴謹的監督以確保安全性)。
>
> 因為**memcpy**因此請謹慎仔細檢查的 VC + + 編譯器和程式庫的使用量，否則就不符合 SDL 的程式碼中會允許這些呼叫。  **memcpy**使用經過審閱由安全性專家時，才符合 SDL 應用程式原始程式碼中導入的呼叫。

**Memcpy**並**wmemcpy**函式就只能被取代，如果常數 **_CRT_SECURE_DEPRECATE_MEMORY**定義之前在順序中包含的陳述式函式已被取代，如下列範例所示：

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

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**memcpy**|\<memory.h> 或 \<string.h>|
|**wmemcpy**|\<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱[memmove](memmove-wmemmove.md)如需如何使用的範例**memcpy**。

## <a name="see-also"></a>另請參閱

[緩衝區操作](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr、wmemchr](memchr-wmemchr.md)<br/>
[memcmp、wmemcmp](memcmp-wmemcmp.md)<br/>
[memmove、wmemmove](memmove-wmemmove.md)<br/>
[memset、wmemset](memset-wmemset.md)<br/>
[strcpy_s、wcscpy_s、_mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
[strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
