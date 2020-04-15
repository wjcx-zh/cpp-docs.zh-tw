---
title: getenv_s, _wgetenv_s
description: 描述 Microsoft Cgetenv_s_wgetenv_s運行時 庫和函數。
ms.date: 4/2/2020
api_name:
- getenv_s
- _wgetenv_s
- _o__wgetenv_s
- _o_getenv_s
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
- getenv_s
- _tgetenv_s
- _wgetenv_s
helpviewer_keywords:
- _tgetenv_s function
- wgetenv_s function
- _wgetenv_s function
- getenv_s function
- environment variables
- tgetenv_s function
ms.assetid: c3ae1ffe-d4cd-4bae-bcb1-3afa754c613a
no-loc:
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
ms.openlocfilehash: 17c4e001f7f4637f6f66f218c94378368976901f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344283"
---
# <a name="getenv_s-_wgetenv_s"></a>getenv_s、_wgetenv_s

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

*p 傳回值*<br/>
所需的緩衝區大小；或者，如果找不到該變數則為 0。

*緩衝區*<br/>
要儲存環境變數值的緩衝區。

*元素數*<br/>
*緩衝區*的大小 。

*瓦爾名稱*<br/>
環境變數名稱。

## <a name="return-value"></a>傳回值

如果成功則為零，否則，如果失敗則為錯誤碼。

### <a name="error-conditions"></a>錯誤狀況

|*p 傳回值*|*緩衝區*|*元素數*|*瓦爾名稱*|傳回值|
|--------------------|--------------|------------------------|---------------|------------------|
|**空**|任意|任意|任意|**埃因瓦爾**|
|任意|**空**|>0|任意|**埃因瓦爾**|
|任意|任意|任意|**空**|**埃因瓦爾**|

任一此種錯誤狀況都會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則函數將**errno**設定為**EINVAL**並傳回**EINVAL**。

此外,如果緩衝區太小,這些函數將返回**ERANGE**。 它們不會叫用無效參數處理常式。 它們在*pReturnValue*中寫入所需的緩衝區大小,從而使程式能夠使用更大的緩衝區再次調用函數。

## <a name="remarks"></a>備註

**getenv_s**函數搜索*變數*的環境變數清單。 **getenv_s**在 Windows 作業系統中不區分大小寫。 **getenv_s**和[_putenv_s](putenv-s-wputenv-s.md)使用全域變數 **_environ**指向的環境副本來訪問環境。 **getenv_s**僅在運行時庫可訪問的數據結構上運行,而不是在作業系統為進程創建的環境"段"上運行。 因此,使用*envp*參數到[主](../../cpp/main-function-command-line-args.md)或[wmain](../../cpp/main-function-command-line-args.md)的程式可能會檢索無效資訊。

**_wgetenv_s**是一個寬字元版本的**getenv_s;****_wgetenv_s**的參數和返回值是寬字元字串。 **_wenviron**全域變數是 **_environ**的寬字元版本。

在 MBCS 程式中(例如,在 SBCS ASCII 程式中 **),_wenviron**最初為**NULL,** 因為環境由多位元位元串組成。 然後,在第一次調用[_wputenv](putenv-wputenv.md)時,或者在第一次調用 **_wgetenv_s**時,如果 (MBCS) 環境已經存在,則創建相應的寬字元字串環境,然後由 **_wenviron**指向 。

同樣,在 Unicode (**_wmain**) 程式中 **,_environ**最初為**NULL,** 因為環境由寬字元字串組成。 然後,在第一次調用[_putenv](putenv-wputenv.md)時,或者在第一次調用getenv_s(Unicode) 環境時,將創建相應的 MBCS 環境,**getenv_s**然後由 **_environ**指向 。

當此環境的兩個複本 (MBCS 和 Unicode) 在此程式中同時存在時，這個執行階段系統必須同時維護兩份複本，造成執行時間較慢。 例如,當您調用 **_putenv**時,也會自動執行對 **_wputenv**的調用,以便兩個環境字串對應。

> [!CAUTION]
> 在罕見情況下，當這個執行階段系統正同時維護此環境的 Unicode 版本和多位元組版本時，這兩個環境版本可能無法完全對應。 這之所以發生，是因為雖然任何唯一的多位元組字元字串會對應到唯一的 Unicode 字串，但從唯一的 Unicode 字串對應到多位元組字元字串並不一定唯一。 如需詳細資訊，請參閱 [_environ、_wenviron](../../c-runtime-library/environ-wenviron.md)。

> [!NOTE]
> **函數的_putenv_s**和 **_getenv_s**系列不具有線程安全性。 **_getenv_s**可以在 **_putenv_s**修改字串時返回字串指標,從而導致隨機失敗。 確定這些函式的呼叫已同步。

在 C++ 中，樣板多載簡化了這些函式的使用方式；此多載可自動推斷緩衝區長度，因此不須指定大小引數。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv_s**|**getenv_s**|**getenv_s**|**_wgetenv_s**|

要檢查或更改**TZ**環境變數的值,請根據需要使用**getenv_s、_putenv****_putenv**和 **_tzset**。 有關**TZ**的詳細資訊,請參閱[_tzset](tzset.md)和[_daylight、_dstbias、_timezone和_tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
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

[處理序和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[環境常數](../../c-runtime-library/environmental-constants.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[_dupenv_s, _wdupenv_s](dupenv-s-wdupenv-s.md)<br/>
