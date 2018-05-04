---
title: getenv、_wgetenv | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- getenv
- _wgetenv
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wgetenv
- getenv
- _tgetenv
dev_langs:
- C++
helpviewer_keywords:
- getenv function
- tgetenv function
- wgetenv function
- environment values
- environment variables
- _tgetenv function
- _wgetenv function
ms.assetid: 3b9cb9ab-a126-4e0e-a44f-6c5a7134daf4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a2e68ca55d9e33995df583719e4797a6880d34ca
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="getenv-wgetenv"></a>getenv、_wgetenv

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

*varname*<br/>
環境變數名稱。

## <a name="return-value"></a>傳回值

讓指標回到環境資料表項目包含*varname*。 使用傳回的指標修改環境變數的值並不安全。 使用[_putenv](putenv-wputenv.md)函式來修改環境變數的值。 傳回值是**NULL**如果*varname*環境資料表中找不到。

## <a name="remarks"></a>備註

**Getenv**函式會搜尋環境變數清單*varname*。 **getenv**不區分大小寫 Windows 作業系統中。 **getenv**和 **_putenv**使用全域變數所指向的環境複製 **_environ**本來存取環境。 **getenv**作業只能在執行階段程式庫可以存取的資料結構，而不是在環境 「 區段 」 處理程序建立的作業系統。 因此，程式使用*envp*引數[主要](../../cpp/main-program-startup.md)或[wmain](../../cpp/main-program-startup.md)可能會擷取無效的資訊。

如果*varname*是**NULL**，此函式叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，此函式會將**errno**至**EINVAL**並傳回**NULL**。

**_wgetenv**是寬字元版本的**getenv**; 的引數和傳回值 **_wgetenv**是寬字元字串。 **_Wenviron**全域變數是寬字元版本的 **_environ**。

在 MBCS 程式中 （例如，在 SBCS ASCII 程式中）， **_wenviron**一開始是**NULL**因為環境以多位元組字元字串所組成。 然後，在第一次呼叫[_wputenv](putenv-wputenv.md)，或在第一個呼叫 **_wgetenv**如果 (MBCS) 環境已經存在，建立對應的寬字元字串環境，並然後指向 **_wenviron**。

同樣地以 Unicode (**_wmain**) 程式， **_environ**一開始是**NULL**因為環境以寬字元字串所組成。 然後，在第一次呼叫 **_putenv**，或在第一個呼叫**getenv**如果 (Unicode) 環境已經存在，建立對應的 MBCS 環境，並再指向 **_environ**。

當此環境的兩個複本 (MBCS 和 Unicode) 在此程式中同時存在時，這個執行階段系統必須同時維護兩份複本，造成執行時間較慢。 例如，每當您呼叫 **_putenv**，呼叫 **_wputenv**也會自動執行，如此這兩個環境字串對應。

> [!CAUTION]
> 在罕見情況下，當這個執行階段系統正同時維護此環境的 Unicode 版本和多位元組版本時，這兩個環境版本可能無法完全對應。 這是因為雖然任何唯一的多位元組字元字串會對應到唯一的 Unicode 字串，但從唯一的 Unicode 字串對應到多位元組字元字串並不一定唯一。 如需詳細資訊，請參閱 [_environ、_wenviron](../../c-runtime-library/environ-wenviron.md)。

> [!NOTE]
> **_Putenv**和 **_getenv**系列的函式不是安全執行緒。 **_getenv**無法傳回字串的指標時 **_putenv**正在修改字串，會導致隨機失敗。 確定這些函式的呼叫已同步。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv**|**getenv**|**getenv**|**_wgetenv**|

若要檢查或變更的值**TZ**環境變數時，使用**getenv**， **_putenv**和 **_tzset**視。 如需有關**TZ**，請參閱[_tzset](tzset.md)和[_daylight、 timezone 和 _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
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

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_putenv、_wputenv](putenv-wputenv.md)<br/>
[環境常數](../../c-runtime-library/environmental-constants.md)<br/>
