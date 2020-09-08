---
title: snprintf、_snprintf、_snprintf_l、_snwprintf、_snwprintf_l
description: Snprintf、_snprintf、_snprintf_l、_snwprintf 和 _snwprintf_的 API 參考;這會將格式化資料寫入字串。
ms.date: 08/27/2020
api_name:
- _snwprintf
- _snprintf
- _snprintf_l
- _snwprintf_l
- snprintf
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
- _snprintf
- snprintf_l
- snwprintf_l
- sntprintf
- snprintf
- _sntprintf
- _sntprintf_l
- sntprintf_l
- snwprintf
- _snprintf_l
- _snwprintf
- _snwprintf_l
helpviewer_keywords:
- snwprintf_l function
- sntprintf_l function
- snprintf_l function
- _snwprintf_l function
- _sntprintf_l function
- _snwprintf function
- _snprintf function
- _sntprintf function
- _snprintf_l function
- snwprintf function
- snprintf function
- sntprintf function
- formatted text [C++]
ms.assetid: 5976c9c8-876e-4ac9-a515-39f3f7fd0925
ms.openlocfilehash: 9a851f08e50d11d3716ea59e00e5e9028b6cd6d5
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556108"
---
# <a name="snprintf-_snprintf-_snprintf_l-_snwprintf-_snwprintf_l"></a>snprintf、_snprintf、_snprintf_l、_snwprintf、_snwprintf_l

將格式化資料寫入字串。 這些函式已有更安全的版本可用，請參閱 [_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)。

## <a name="syntax"></a>語法

```C
int snprintf(
   char *buffer,
   size_t count,
   const char *format [,
   argument] ...
);
int _snprintf(
   char *buffer,
   size_t count,
   const char *format [,
   argument] ...
);
int _snprintf_l(
   char *buffer,
   size_t count,
   const char *format,
   locale_t locale [,
   argument] ...
);
int _snwprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format [,
   argument] ...
);
int _snwprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
template <size_t size>
int _snprintf(
   char (&buffer)[size],
   size_t count,
   const char *format [,
   argument] ...
); // C++ only
template <size_t size>
int _snprintf_l(
   char (&buffer)[size],
   size_t count,
   const char *format,
   locale_t locale [,
   argument] ...
); // C++ only
template <size_t size>
int _snwprintf(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format [,
   argument] ...
); // C++ only
template <size_t size>
int _snwprintf_l(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
); // C++ only
```

### <a name="parameters"></a>參數

*緩衝區*<br/>
輸出的儲存位置。

*計數*<br/>
要儲存的最大字元數。

*format*<br/>
格式控制字串。

*引數*<br/>
選擇性引數。

*locale*<br/>
要使用的地區設定。

如需詳細資訊，請參閱[格式規格語法：printf 和 wprintf 函式](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

## <a name="return-value"></a>傳回值

讓 **len** 成為格式化資料字串的長度，不包括終止的 null。 **Len**和**count**都是**snprintf**和 **_snprintf**的字元數，以及 **_snwprintf**的寬字元數。

針對所有函式，如果**len**  <  *計數*， **len**字元會儲存在*緩衝區*中，則會附加 null 結束字元，並傳回**len** 。

當**len**大於或等於*count*時， **snprintf**函式會藉由將 null 結束字元放置於來截斷輸出 `buffer[count-1]` 。 傳回的值是 **len**，如果 *count* 夠大，則會輸出的字元數。 如果發生編碼錯誤， **snprintf** 函數會傳回負值。

針對**snprintf**以外的所有函式，如果**len**  =  *計數*， **len**字元會儲存在*緩衝區*中，不會附加 null 結束字元，並且傳回**len** 。 如果**len**  >  *計數*， *count*字元會儲存在*緩衝區*中，不會附加 null 結束字元，並且傳回負值。

如果 *緩衝區* 是 null 指標，且 *計數* 為零，則會以格式化輸出所需的字元數（不包括終止的 null）傳回 **len** 。 若要使用相同的 *引數* 和 *地區* 設定參數進行成功呼叫，請配置至少保留 **len** + 1 個字元的緩衝區。

如果 *緩衝區* 為 null 指標，且 *計數* 為非零值，或如果 *格式* 為 null 指標，則會叫用不正確參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會傳回-1，並將 **errno** 設定為 **EINVAL**。

如需這些錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Snprintf**函式和 **_snprintf**系列的函式會在*緩衝區*中格式化和儲存*計數*或較少的字元。 **Snprintf**函式一律會儲存結束的 null 字元，必要時也會截斷輸出。 如果格式化的字串長度嚴格小於*count*個字元，則 **_snprintf**系列的函式只會附加終止的 null 字元。 每個 *引數* 都會 (是否轉換任何) ，而且會根據 *格式*的對應格式規格來輸出。 格式是由一般字元所組成，而且具有與[printf](printf-printf-l-wprintf-wprintf-l.md)的*格式*引數相同的形式和功能。 如果在重疊的字串之間進行複製，則行為是未定義的。

> [!IMPORTANT]
> 確認 *format* 不是使用者定義的字串。 由於 **_snprintf** 函式並不保證 null 結束，尤其是當傳回值為 *count*時，請確定它們後面接著加入 null 結束字元的程式碼。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/win32/SecBP/avoiding-buffer-overruns)。

從 Visual Studio 2015 和 Windows 10 的 UCRT 開始， **snprintf** 不再等同于 **_snprintf**。 **Snprintf**函式的行為現在符合 C99 標準。

**_snwprintf** 是寬字元版本的 **_snprintf**; **_snwprintf** 的指標引數是寬字元字串。 偵測 **_snwprintf** 中的編碼錯誤可能與 **_snprintf**中的編碼錯誤不同。 **_snwprintf**，就像 **swprintf**一樣，會將輸出寫入字串，而不是 **檔**類型的目的地。

這些具有 **_l** 尾碼的函式版本都相同，不同之處在于它們會使用傳入的地區設定參數，而不是目前的執行緒地區設定。

在 C++ 中，這些函式具有多載樣板，可以叫用更新、更安全的相對版本。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_sntprintf**|**_snprintf**|**_snprintf**|**_snwprintf**|
|**_sntprintf_l**|**_snprintf_l**|**_snprintf_l**|**_snwprintf_l**|

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**snprintf**、 **_snprintf**、  **_snprintf_l**|\<stdio.h>|
|**_snwprintf**， **_snwprintf_l**|\<stdio.h> 或 \<wchar.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_snprintf.c
// compile with: /W3
#include <stdio.h>
#include <stdlib.h>

#if !defined(__cplusplus)
typedef int bool;
const bool true = 1;
const bool false = 0;
#endif

#define FAIL 0 // change to 1 and see what happens

int main(void)
{
   char buffer[200];
   const static char s[] = "computer"
#if FAIL
"computercomputercomputercomputercomputercomputercomputercomputer"
"computercomputercomputercomputercomputercomputercomputercomputer"
"computercomputercomputercomputercomputercomputercomputercomputer"
"computercomputercomputercomputercomputercomputercomputercomputer"
#endif
   ;
   const char c = 'l';
   const int i = 35;
#if FAIL
   const double fp = 1e300; // doesn't fit in the buffer
#else
   const double fp = 1.7320534;
#endif
   /* !subtract one to prevent "squeezing out" the terminal null! */
   const int bufferSize = sizeof(buffer)/sizeof(buffer[0]) - 1;
   int bufferUsed = 0;
   int bufferLeft = bufferSize - bufferUsed;
   bool bSuccess = true;
   buffer[0] = 0;

   /* Format and print various data: */

   if (bufferLeft > 0)
   {
      int perElementBufferUsed = _snprintf(&buffer[bufferUsed],
      bufferLeft, "   String: %s\n", s ); // C4996
      // Note: _snprintf is deprecated; consider _snprintf_s instead
      if (bSuccess = (perElementBufferUsed >= 0))
      {
         bufferUsed += perElementBufferUsed;
         bufferLeft -= perElementBufferUsed;
         if (bufferLeft > 0)
         {
            int perElementBufferUsed = _snprintf(&buffer[bufferUsed],
            bufferLeft, "   Character: %c\n", c ); // C4996
            if (bSuccess = (perElementBufferUsed >= 0))
            {
               bufferUsed += perElementBufferUsed;
               bufferLeft -= perElementBufferUsed;
               if (bufferLeft > 0)
               {
                  int perElementBufferUsed = _snprintf(&buffer
                  [bufferUsed], bufferLeft, "   Integer: %d\n", i ); // C4996
                  if (bSuccess = (perElementBufferUsed >= 0))
                  {
                     bufferUsed += perElementBufferUsed;
                     bufferLeft -= perElementBufferUsed;
                     if (bufferLeft > 0)
                     {
                        int perElementBufferUsed = _snprintf(&buffer
                        [bufferUsed], bufferLeft, "   Real: %f\n", fp ); // C4996
                        if (bSuccess = (perElementBufferUsed >= 0))
                        {
                           bufferUsed += perElementBufferUsed;
                        }
                     }
                  }
               }
            }
         }
      }
   }

   if (!bSuccess)
   {
      printf("%s\n", "failure");
   }
   else
   {
      /* !store null because _snprintf doesn't necessarily (if the string
       * fits without the terminal null, but not with it)!
       * bufferUsed might be as large as bufferSize, which normally is
       * like going one element beyond a buffer, but in this case
       * subtracted one from bufferSize, so we're ok.
       */
      buffer[bufferUsed] = 0;
      printf( "Output:\n%s\ncharacter count = %d\n", buffer, bufferUsed );
   }
   return EXIT_SUCCESS;
}
```

```Output
Output:
   String: computer
   Character: l
   Integer: 35
   Real: 1.732053

character count = 69
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf、_sscanf_l、swscanf、_swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf 函式](../../c-runtime-library/vprintf-functions.md)<br/>
