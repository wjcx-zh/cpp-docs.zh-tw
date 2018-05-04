---
title: getenv_s、_wgetenv_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- getenv_s
- _wgetenv_s
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
- getenv_s
- _tgetenv_s
- _wgetenv_s
dev_langs:
- C++
helpviewer_keywords:
- _tgetenv_s function
- wgetenv_s function
- _wgetenv_s function
- getenv_s function
- environment variables
- tgetenv_s function
ms.assetid: c3ae1ffe-d4cd-4bae-bcb1-3afa754c613a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 144c8d1d05d40f17e37f337902bbd2ee2cf15458
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="getenvs-wgetenvs"></a>getenv_s、_wgetenv_s

從目前的環境取得值。 這些版本的 [getenv、_wgetenv](getenv-wgetenv.md) 具有安全性增強功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
errno_t getenv_s(
   size_t *pReturnValue,
   char* buffer,
   size_t numberOfElements,
   const char *varname
);
errno_t _wgetenv_s(
   size_t *pReturnValue,
   wchar_t *buffer,
   size_t numberOfElements,
   const wchar_t *varname
);
template <size_t size>
errno_t getenv_s(
   size_t *pReturnValue,
   char (&buffer)[size],
   const char *varname
); // C++ only
template <size_t size>
errno_t _wgetenv_s(
   size_t *pReturnValue,
   wchar_t (&buffer)[size],
   const wchar_t *varname
); // C++ only
```

### <a name="parameters"></a>參數

*pReturnValue*<br/>
所需的緩衝區大小；或者，如果找不到該變數則為 0。

*buffer*<br/>
要儲存環境變數值的緩衝區。

*numberOfElements*<br/>
大小*緩衝區*。

*varname*<br/>
環境變數名稱。

## <a name="return-value"></a>傳回值

如果成功則為零，否則，如果失敗則為錯誤碼。

### <a name="error-conditions"></a>錯誤狀況

|*pReturnValue*|*buffer*|*numberOfElements*|*varname*|傳回值|
|--------------------|--------------|------------------------|---------------|------------------|
|**NULL**|任何|任何|任何|**EINVAL**|
|任何|**NULL**|>0|任何|**EINVAL**|
|任何|任何|任何|**NULL**|**EINVAL**|

任一此種錯誤狀況都會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，函式會將**errno**至**EINVAL**並傳回**EINVAL**。

此外，如果緩衝區太小，這些函式會傳回**為 ERANGE**。 它們不會叫用無效參數處理常式。 寫出所需的緩衝區大小，以*pReturnValue*，並藉此啟用，呼叫一次具有較大的緩衝區的函式。

## <a name="remarks"></a>備註

**Getenv_s**函式會搜尋環境變數清單*varname*。 **getenv_s**不區分大小寫 Windows 作業系統中。 **getenv_s**和[_putenv_s](putenv-s-wputenv-s.md)使用全域變數所指向的環境複製 **_environ**本來存取環境。 **getenv_s**作業只能在執行階段程式庫可以存取的資料結構，而不是在環境 「 區段 」 所建立的作業系統處理序。 因此，程式使用*envp*引數[主要](../../cpp/main-program-startup.md)或[wmain](../../cpp/main-program-startup.md)可能會擷取無效的資訊。

**_wgetenv_s**是寬字元版本的**getenv_s**; 的引數和傳回值 **_wgetenv_s**是寬字元字串。 **_Wenviron**全域變數是寬字元版本的 **_environ**。

在 MBCS 程式中 （例如，在 SBCS ASCII 程式中）， **_wenviron**一開始是**NULL**因為環境以多位元組字元字串所組成。 然後，在第一次呼叫[_wputenv](putenv-wputenv.md)，或在第一個呼叫 **_wgetenv_s**，如果 (MBCS) 環境已經存在，建立對應的寬字元字串環境，然後指向 **_wenviron**。

同樣地以 Unicode (**_wmain**) 程式， **_environ**一開始是**NULL**因為環境以寬字元字串所組成。 然後，在第一次呼叫[_putenv](putenv-wputenv.md)，或在第一個呼叫**getenv_s**如果 (Unicode) 環境已經存在，建立對應的 MBCS 環境，並再指向 **_environ**。

當此環境的兩個複本 (MBCS 和 Unicode) 在此程式中同時存在時，這個執行階段系統必須同時維護兩份複本，造成執行時間較慢。 例如，當您呼叫 **_putenv**，呼叫 **_wputenv**也會自動執行，讓這兩個環境字串對應。

> [!CAUTION]
> 在罕見情況下，當這個執行階段系統正同時維護此環境的 Unicode 版本和多位元組版本時，這兩個環境版本可能無法完全對應。 這之所以發生，是因為雖然任何唯一的多位元組字元字串會對應到唯一的 Unicode 字串，但從唯一的 Unicode 字串對應到多位元組字元字串並不一定唯一。 如需詳細資訊，請參閱 [_environ、_wenviron](../../c-runtime-library/environ-wenviron.md)。

> [!NOTE]
> **_Putenv_s**和 **_getenv_s**系列的函式不是安全執行緒。 **_getenv_s**無法傳回字串的指標時 **_putenv_s**正在修改字串，並因而導致隨機失敗。 確定這些函式的呼叫已同步。

在 C++ 中，樣板多載簡化了這些函式的使用方式；此多載可自動推斷緩衝區長度，因此不須指定大小引數。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv_s**|**getenv_s**|**getenv_s**|**_wgetenv_s**|

若要檢查或變更的值**TZ**環境變數時，使用**getenv_s**， **_putenv**，和 **_tzset**、 視需要而定。 如需有關**TZ**，請參閱[_tzset](tzset.md)和[_daylight、 _dstbias、 _timezone 和 _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**getenv_s**|\<stdlib.h>|
|**_wgetenv_s**|\<stdlib.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_getenv_s.c
// This program uses getenv_s to retrieve
// the LIB environment variable and then uses
// _putenv to change it to a new value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char* libvar;
   size_t requiredSize;

   getenv_s( &requiredSize, NULL, 0, "LIB");
   if (requiredSize == 0)
   {
      printf("LIB doesn't exist!\n");
      exit(1);
   }

   libvar = (char*) malloc(requiredSize * sizeof(char));
   if (!libvar)
   {
      printf("Failed to allocate memory!\n");
      exit(1);
   }

   // Get the value of the LIB environment variable.
   getenv_s( &requiredSize, libvar, requiredSize, "LIB" );

   printf( "Original LIB variable is: %s\n", libvar );

   // Attempt to change path. Note that this only affects
   // the environment variable of the current process. The command
   // processor's environment is not changed.
   _putenv_s( "LIB", "c:\\mylib;c:\\yourlib" );

   getenv_s( &requiredSize, NULL, 0, "LIB");

   libvar = (char*) realloc(libvar, requiredSize * sizeof(char));
   if (!libvar)
   {
      printf("Failed to allocate memory!\n");
      exit(1);
   }

   // Get the new value of the LIB environment variable.
   getenv_s( &requiredSize, libvar, requiredSize, "LIB" );

   printf( "New LIB variable is: %s\n", libvar );

   free(libvar);
}
```

```Output
Original LIB variable is: c:\vctools\lib;c:\vctools\atlmfc\lib;c:\vctools\PlatformSDK\lib;c:\vctools\Visual Studio SDKs\DIA Sdk\lib;c:\vctools\Visual Studio SDKs\BSC Sdk\lib
New LIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[環境常數](../../c-runtime-library/environmental-constants.md)<br/>
[_putenv、_wputenv](putenv-wputenv.md)<br/>
[_dupenv_s、_wdupenv_s](dupenv-s-wdupenv-s.md)<br/>
