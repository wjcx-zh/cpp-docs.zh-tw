---
title: _cscanf_s、_cscanf_s_l、_cwscanf_s、_cwscanf_s_l
ms.date: 11/04/2016
api_name:
- _cwscanf_s_l
- _cwscanf_s
- _cscanf_s
- _cscanf_s_l
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- cscanf_s
- cscanf_s_l
- cwscanf_s
- _cwscanf_s
- _tcscanf_s
- _cscanf_s
- _cwscanf_s_l
- _cscanf_s_l
- cwscanf_s_l
- _tcscanf_s_l
- tcscanf_s
- tcscanf_s_l
helpviewer_keywords:
- cscanf_s function
- _cwscanf_s_l function
- tcscanf_s function
- console [C++], reading from
- _cscanf_s function
- data [C++], reading from the console
- cwscanf_s function
- _tcscanf_s_l function
- _cscanf_s_l function
- cscanf_s_l function
- cwscanf_s_l function
- reading data [C++], from the console
- _cwscanf_s function
- _tcscanf_s function
- tcscanf_s_l function
ms.assetid: 9ccab74d-916f-42a6-93d8-920525efdf4b
ms.openlocfilehash: a869ae4ab1b5f81c4198f620662604b79f19c2ab
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234233"
---
# <a name="_cscanf_s-_cscanf_s_l-_cwscanf_s-_cwscanf_s_l"></a>_cscanf_s、_cscanf_s_l、_cwscanf_s、_cwscanf_s_l

從主控台讀取格式化資料。 這些是具有如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的更安全 [_cscanf、_cscanf_l、_cwscanf、_cwscanf_l](cscanf-cscanf-l-cwscanf-cwscanf-l.md) 版本。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _cscanf_s(
   const char *format [,
   argument] ...
);
int _cscanf_s_l(
   const char *format,
   locale_t locale [,
   argument] ...
);
int _cwscanf_s(
   const wchar_t *format [,
   argument] ...
);
int _cwscanf_s_l(
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
```

### <a name="parameters"></a>參數

*format*<br/>
格式控制字串。

*引數*<br/>
選擇性參數。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

已成功轉換並指派的欄位數目。 此傳回值不包含已讀取但未指派的欄位。 傳回值為**EOF** ，用於嘗試讀取檔案結尾。 當鍵盤輸入在作業系統命令列層級重新導向時，就會發生此情況。 傳回值 0 表示未指派任何欄位。

這些函式會驗證它們的參數。 如果*format*是 null 指標，則這些函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會傳回**EOF** ，而**errno**會設為**EINVAL**。

## <a name="remarks"></a>備註

**_Cscanf_s**函式會直接從主控台將資料讀取至*引數*所指定的位置。 [_getche](getch-getwch.md)函式可用來讀取字元。 每個選擇性參數都必須是變數的指標，其類型會對應至*格式*的類型規範。 格式會控制輸入欄位的轉譯，並具有與[scanf_s](scanf-scanf-l-wscanf-wscanf-l.md)函式的*格式*參數相同的形式和功能。 雖然 **_cscanf_s**通常會回應輸入字元，但如果最後一次呼叫是要 **_ungetch**，就不會這麼做。

就像**scanf**系列中其他安全版本的函式一樣， **_cscanf_s**和 **_cswscanf_s**需要類型欄位字元**c**、 **c**、 **s**、 **s**和 **[** 的大小引數。 如需詳細資訊，請參閱 [scanf 寬度規格](../../c-runtime-library/scanf-width-specification.md)。

> [!NOTE]
> Size 參數的類型為 **`unsigned`** ，而不是**size_t**。

這些具有 **_l**尾碼的函式版本都相同，不同之處在于它們會使用傳入的地區設定參數，而不是目前的執行緒地區設定。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcscanf_s**|**_cscanf_s**|**_cscanf_s**|**_cwscanf_s**|
|**_tcscanf_s_l**|**_cscanf_s_l**|**_cscanf_s_l**|**_cwscanf_s_l**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_cscanf_s**， **_cscanf_s_l**|\<conio.h>|
|**_cwscanf_s**， **_cwscanf_s_l**|\<conio.h> 或 \<wchar.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_cscanf_s.c
// compile with: /c
/* This program prompts for a string
* and uses _cscanf_s to read in the response.
* Then _cscanf_s returns the number of items
* matched, and the program displays that number.
*/

#include <stdio.h>
#include <conio.h>

int main( void )
{
   int result, n[3];
   int i;

   result = _cscanf_s( "%i %i %i", &n[0], &n[1], &n[2] );
   _cprintf_s( "\r\nYou entered " );
   for( i=0; i<result; i++ )
      _cprintf_s( "%i ", n[i] );
   _cprintf_s( "\r\n" );
}
```

```Input
1 2 3
```

```Output
You entered 1 2 3
```

## <a name="see-also"></a>另請參閱

[主控台和埠 i/o](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cprintf、_cprintf_l、_cwprintf、_cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fscanf_s、_fscanf_s_l、fwscanf_s、_fwscanf_s_l](fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)<br/>
[scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
