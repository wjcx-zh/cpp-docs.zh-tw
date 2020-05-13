---
title: _cputs、_cputws
ms.date: 4/2/2020
api_name:
- _cputws
- _cputs
- _o__cputs
- _o__cputws
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
- api-ms-win-crt-conio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- cputws
- _cputs
- _cputws
helpviewer_keywords:
- strings [C++], writing
- _cputs function
- _cputws function
- putting strings to the console
- cputs function
- console, sending strings to
- cputws function
ms.assetid: ec418484-0f8d-43ec-8d8b-198a556c659e
ms.openlocfilehash: 469b39e4e08f13af8d8ac3e679ed55c7afb240d2
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917608"
---
# <a name="_cputs-_cputws"></a>_cputs、_cputws

將字串放入主控台。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _cputs(
   const char *str
);
int _cputws(
   const wchar_t *str
);
```

### <a name="parameters"></a>參數

*str*<br/>
輸出字串。

## <a name="return-value"></a>傳回值

如果成功， **_cputs**會傳回0。 如果函式失敗，則會傳回非零值。

## <a name="remarks"></a>備註

**_Cputs**函式會將*str*直接指向的以 null 結束的字串寫入主控台。 歸位字元-換行字元 (CR-LF) 組合不會自動附加至字串。

這個函式會驗證其參數。 如果*str*為**Null**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **errno**會設為**EINVAL** ，並傳回-1。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_cputts**|**_cputs**|**_cputs**|**_cputws**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_cputs**|\<conio.h>|\<errno.h>|
|**_cputws**|\<conio.h>|\<errno.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_cputs.c
// compile with: /c
// This program first displays a string to the console.

#include <conio.h>
#include <errno.h>

void print_to_console(char* buffer)
{
   int retval;
   retval = _cputs( buffer );
   if (retval)
   {
       if (errno == EINVAL)
       {
         _cputs( "Invalid buffer in print_to_console.\r\n");
       }
       else
         _cputs( "Unexpected error in print_to_console.\r\n");
   }
}

void wprint_to_console(wchar_t* wbuffer)
{
   int retval;
   retval = _cputws( wbuffer );
   if (retval)
   {
       if (errno == EINVAL)
       {
         _cputws( L"Invalid buffer in wprint_to_console.\r\n");
       }
       else
         _cputws( L"Unexpected error in wprint_to_console.\r\n");
   }
}

int main()
{

   // String to print at console.
   // Notice the \r (return) character.
   char* buffer = "Hello world (courtesy of _cputs)!\r\n";
   wchar_t *wbuffer = L"Hello world (courtesy of _cputws)!\r\n";
   print_to_console(buffer);
   wprint_to_console( wbuffer );
}
```

```Output
Hello world (courtesy of _cputs)!
Hello world (courtesy of _cputws)!
```

## <a name="see-also"></a>另請參閱

[主控台和埠 i/o](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_putch、_putwch](putch-putwch.md)<br/>
