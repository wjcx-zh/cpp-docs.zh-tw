---
title: _cscanf、_cscanf_l、_cwscanf、_cwscanf_l
ms.date: 10/21/2019
api_name:
- _cscanf_l
- _cscanf
- _cwscanf
- _cwscanf_l
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
- _cwscanf
- cwscanf_l
- tcscanf_l
- _tcscanf_l
- _cscanf
- _cscanf_l
- tcscanf
- cwscanf
- _cwscanf_l
- cscanf_l
- _tcscanf
helpviewer_keywords:
- _cwscanf function
- data [C++], reading from the console
- cscanf_l function
- tcscanf function
- _cscanf_l function
- cwscanf function
- _tcscanf_l function
- _cscanf function
- _tcscanf function
- cwscanf_l function
- tcscanf_l function
- reading data [C++], from the console
- _cwscanf_l function
ms.assetid: dbfe7547-b577-4567-a1cb-893fa640e669
ms.openlocfilehash: 45dcbd93ab689c8c86ab35e53552a65f561dfd18
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234246"
---
# <a name="_cscanf-_cscanf_l-_cwscanf-_cwscanf_l"></a>_cscanf、_cscanf_l、_cwscanf、_cwscanf_l

從主控台讀取格式化資料。 這些函式已有更安全的版本可用；請參閱 [_cscanf_s、_cscanf_s_l、_cwscanf_s、_cwscanf_s_l](cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)。

> [!NOTE]
> 在 Visual Studio 2015 中， `printf` 和系列函式已宣告為， `scanf` **`inline`** 並已移至 `<stdio.h>` 和 `<conio.h>` 標頭。 如果您要遷移較舊的程式碼，您可能會看到與這些函式的連接有*LNK2019* 。 如需詳細資訊，請參閱[Visual C++ 變更歷程記錄 2003-2015](../../porting/visual-cpp-change-history-2003-2015.md#stdio_and_conio)。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _cscanf(
   const char *format [,
   argument] ...
);
int _cscanf_l(
   const char *format,
   locale_t locale [,
   argument] ...
);
int _cwscanf(
   const wchar_t *format [,
   argument] ...
);
int _cwscanf_l(
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

## <a name="remarks"></a>備註

**_Cscanf**函式會直接從主控台將資料讀取至*引數*所指定的位置。 [_getche](getch-getwch.md)函式可用來讀取字元。 每個選擇性參數都必須是變數的指標，其類型會對應至*格式*的類型規範。 格式會控制輸入欄位的轉譯，並具有與[scanf](scanf-scanf-l-wscanf-wscanf-l.md)函式的*格式*參數相同的形式和功能。 雖然 **_cscanf**通常會回應輸入字元，但如果最後一次呼叫是要 **_ungetch**，就不會這麼做。

這個函式會驗證它的參數。 如果 format 為**Null**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **errno**會設為**EINVAL** ，而函數會傳回**EOF**。

這些具有 **_l**尾碼的函式版本都相同，不同之處在于它們會使用傳入的地區設定參數，而不是目前的執行緒地區設定。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcscanf**|**_cscanf**|**_cscanf**|**_cwscanf**|
|**_tcscanf_l**|**_cscanf_l**|**_cscanf_l**|**_cwscanf_l**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_cscanf**， **_cscanf_l**|\<conio.h>|
|**_cwscanf**， **_cwscanf_l**|\<conio.h> 或 \<wchar.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_cscanf.c
// compile with: /c /W3
/* This program prompts for a string
* and uses _cscanf to read in the response.
* Then _cscanf returns the number of items
* matched, and the program displays that number.
*/

#include <stdio.h>
#include <conio.h>

int main( void )
{
   int   result, i[3];

   _cprintf_s( "Enter three integers: ");
   result = _cscanf( "%i %i %i", &i[0], &i[1], &i[2] ); // C4996
   // Note: _cscanf is deprecated; consider using _cscanf_s instead
   _cprintf_s( "\r\nYou entered " );
   while( result-- )
      _cprintf_s( "%i ", i[result] );
   _cprintf_s( "\r\n" );
}
```

```Input
1 2 3
```

```Output
Enter three integers: 1 2 3
You entered 3 2 1
```

## <a name="see-also"></a>另請參閱

[主控台和埠 i/o](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cprintf、_cprintf_l、_cwprintf、_cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fscanf、_fscanf_l、fwscanf、_fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[sscanf、_sscanf_l、swscanf、_swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
