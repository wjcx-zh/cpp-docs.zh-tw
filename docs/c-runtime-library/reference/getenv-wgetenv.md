---
title: getenv, _wgetenv
description: 描述 Microsoft Cgetenv_wgetenv運行時 庫和函數。
ms.date: 4/2/2020
api_name:
- getenv
- _wgetenv
- _o__wgetenv
- _o_getenv
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wgetenv
- getenv
- _tgetenv
helpviewer_keywords:
- getenv function
- tgetenv function
- wgetenv function
- environment values
- environment variables
- _tgetenv function
- _wgetenv function
ms.assetid: 3b9cb9ab-a126-4e0e-a44f-6c5a7134daf4
no-loc:
- getenv
- _wgetenv
- getenv_s
- _wgetenv_s
- _putenv_s
- main
- wmain
- errno
- EINVAL
- ERANGE
- _environ
- _wenviron
- _putenv
- _wputenv
- _tgetenv_s
- _tzset
- _dupenv_s
- _wdupenv_s
ms.openlocfilehash: c9d7f7e1a2c5d6b15aee2f7f972a30cc0c90115c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344259"
---
# <a name="getenv-_wgetenv"></a>getenv、_wgetenv

從目前的環境取得值。 這些函式已有更安全的版本，請參閱 [getenv_s、_wgetenv_s](getenv-s-wgetenv-s.md)。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
char *getenv(
   const char *varname
);
wchar_t *_wgetenv(
   const wchar_t *varname
);
```

### <a name="parameters"></a>參數

*瓦爾名稱*<br/>
環境變數名稱。

## <a name="return-value"></a>傳回值

返回指向包含*varname*的環境表條目的指標。 使用傳回的指標修改環境變數的值並不安全。 使用[_putenv](putenv-wputenv.md)函數修改環境變數的值。 如果在環境表中找不到*varname,* 則傳回值為**NULL。**

## <a name="remarks"></a>備註

**getenv**函數搜尋變數環境變數的清單,以搜尋*varname*。 **getenv**在 Windows 作業系統中不區分大小寫。 **getenv**和 **_putenv**使用全域變數 **_environ**指向的環境的副本來訪問環境。 **getenv**僅在執行時庫可存取的數據結構上運行,而不是作業系統為進程創建的環境"段"上運行。 因此,使用*envp*參數到[主](../../cpp/main-function-command-line-args.md)或[wmain](../../cpp/main-function-command-line-args.md)的程式可能會檢索無效資訊。

如果*varname*為**NULL,** 則此函數將呼叫無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,此函數將**errno**設定到**EINVAL**並傳回**NULL**。

**_wgetenv**是**getenv**的寬字元版本;**_wgetenv**的參數和返回值是寬字元字串。 **_wenviron**全域變數是 **_environ**的寬字元版本。

在 MBCS 程式中(例如,在 SBCS ASCII 程式中 **),_wenviron**最初為**NULL,** 因為環境由多位元位元串組成。 然後,在第一次調用[_wputenv](putenv-wputenv.md)時,或者在第一次調用 **_wgetenv**如果 (MBCS) 環境已經存在時,將建立相應的寬字元字串環境,然後由 **_wenviron**指向 。

同樣,在 Unicode (**_wmain**) 程式中 **,_environ**最初為**NULL,** 因為環境由寬字元字串組成。 然後,在第一次調用 **_putenv**時,或者在第一次調用**getenv**時(如果(Unicode) 環境已經存在,則創建相應的 MBCS 環境,然後由 **_environ**指向 。

當此環境的兩個複本 (MBCS 和 Unicode) 在此程式中同時存在時，這個執行階段系統必須同時維護兩份複本，造成執行時間較慢。 例如,每當調用 **_putenv**時,也會自動執行對 **_wputenv**的調用,以便兩個環境字串對應。

> [!CAUTION]
> 在罕見情況下，當這個執行階段系統正同時維護此環境的 Unicode 版本和多位元組版本時，這兩個環境版本可能無法完全對應。 這是因為雖然任何唯一的多位元組字元字串會對應到唯一的 Unicode 字串，但從唯一的 Unicode 字串對應到多位元組字元字串並不一定唯一。 如需詳細資訊，請參閱 [_environ、_wenviron](../../c-runtime-library/environ-wenviron.md)。

> [!NOTE]
> **函數的_putenv**和 **_getenv**系列不具有線程安全。 **_getenv**可以在 **_putenv**修改字串時返回字串指標,從而導致隨機失敗。 確定這些函式的呼叫已同步。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv**|**getenv**|**getenv**|**_wgetenv**|

要檢查或更改**TZ**環境變數的值,請根據需要使用**getenv、_putenv**和 **_putenv****_tzset。** 有關**TZ**的詳細資訊,請參閱[_tzset](tzset.md)和[_daylight、時區和_tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**getenv**|\<stdlib.h>|
|**_wgetenv**|\<stdlib.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_getenv.c
// compile with: /W3
// This program uses getenv to retrieve
// the LIB environment variable and then uses
// _putenv to change it to a new value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *libvar;

   // Get the value of the LIB environment variable.
   libvar = getenv( "LIB" ); // C4996
   // Note: getenv is deprecated; consider using getenv_s instead

   if( libvar != NULL )
      printf( "Original LIB variable is: %s\n", libvar );

   // Attempt to change path. Note that this only affects the environment
   // variable of the current process. The command processor's
   // environment is not changed.
   _putenv( "LIB=c:\\mylib;c:\\yourlib" ); // C4996
   // Note: _putenv is deprecated; consider using putenv_s instead

   // Get new value.
   libvar = getenv( "LIB" ); // C4996

   if( libvar != NULL )
      printf( "New LIB variable is: %s\n", libvar );
}
```

```Output
Original LIB variable is: C:\progra~1\devstu~1\vc\lib
New LIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>另請參閱

[程序與環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[環境常數](../../c-runtime-library/environmental-constants.md)<br/>
