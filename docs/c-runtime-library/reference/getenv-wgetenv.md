---
title: "getenv、_wgetenv | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 31
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 76db8cf45132bc76ab56028eb139585ca663c68d
ms.lasthandoff: 02/24/2017

---
# <a name="getenv-wgetenv"></a>getenv、_wgetenv
從目前的環境取得值。 這些函式已有更安全的版本，請參閱 [getenv_s、_wgetenv_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md)。  
  
> [!IMPORTANT]
>  這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
char *getenv(   
   const char *varname   
);  
wchar_t *_wgetenv(   
   const wchar_t *varname   
);  
```  
  
#### <a name="parameters"></a>參數  
 `varname`  
 環境變數名稱。  
  
## <a name="return-value"></a>傳回值  
 將指標傳回至包含 `varname` 的環境資料表項目。 使用傳回的指標修改環境變數的值並不安全。 使用 `_putenv` 函式修改環境變數的值。 如果在環境資料表中找不到 `varname`，則傳回值是 `NULL`。  
  
## <a name="remarks"></a>備註  
 `getenv` 函式會在環境變數清單中搜尋 `varname`。 `getenv` 在 Windows 作業系統中不區分大小寫。 `getenv` 和 `_putenv` 使用全域變數 `_environ` 所指出的環境複本來存取環境。 `getenv` 只會在執行階段程式庫可以存取的資料結構上運作，而不會在作業系統為此處理序所建立的環境「區段」上運作。 因此，對 [main](../../cpp/main-program-startup.md) 或 [wmain](../../cpp/main-program-startup.md) 使用 `envp` 引數的程式可能會擷取無效資訊。  
  
 如果 `varname` 為 `NULL`，此函式會呼叫無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，此函式會將 `errno` 設為 `EINVAL`，並傳回 `NULL`。  
  
 `_wgetenv` 是 `getenv` 的寬字元版本，`_wgetenv` 的引數與傳回值是寬字元字串。 `_wenviron` 全域變數是寬字元版本的 `_environ`。  
  
 在 MBCS 程式中 (例如，在 SBCS ASCII 程式中)，`_wenviron` 一開始是 `NULL`，因為此環境由多位元組字元字串所組成。 然後，在第一次呼叫 `_wputenv` 時，或在第一次呼叫 `_wgetenv` 時，如果 (MBCS) 環境已經存在，則會建立對應的寬字元字串環境，然後由 `_wenviron` 指向該變數。  
  
 同樣地，在 Unicode (`_wmain`) 程式中，`_environ` 一開始是 `NULL`，因為此環境由寬字元字串所組成。 然後，在第一次呼叫 `_putenv` 時，或在第一次呼叫 `getenv` 時，如果 (Unicode) 環境已經存在，則會建立對應的 MBCS 環境，然後再由 `_environ` 指向該變數。  
  
 當此環境的兩個複本 (MBCS 和 Unicode) 在此程式中同時存在時，這個執行階段系統必須同時維護兩份複本，造成執行時間較慢。 例如，每當您呼叫 `_putenv` 時，也會自動執行對 `_wputenv` 的呼叫，使得這兩個環境字串對應。  
  
> [!CAUTION]
>  在罕見情況下，當這個執行階段系統正同時維護此環境的 Unicode 版本和多位元組版本時，這兩個環境版本可能無法完全對應。 這是因為雖然任何唯一的多位元組字元字串會對應到唯一的 Unicode 字串，但從唯一的 Unicode 字串對應到多位元組字元字串並不一定唯一。 如需詳細資訊，請參閱 [_environ、_wenviron](../../c-runtime-library/environ-wenviron.md)。  
  
> [!NOTE]
>  `_putenv` 和 `_getenv` 系列的函式不是安全執行緒。 `_putenv` 正在修改字串時，`_getenv` 可能會傳回字串指標，因而導致隨機失敗。 確定這些函式的呼叫已同步。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tgetenv`|`getenv`|`getenv`|`_wgetenv`|  
  
 若要檢查或變更 `TZ` 環境變數的值，請視需要使用 `getenv`、`_putenv` 和 `_tzset`。 如需 `TZ` 的詳細資訊，請參閱 [_tzset](../../c-runtime-library/reference/tzset.md) 和 [_daylight、timezone 和 _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`getenv`|\<stdlib.h>|  
|`_wgetenv`|\<stdlib.h> 或 \<wchar.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
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
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 [System::Environment::GetEnvironmentVariable](https://msdn.microsoft.com/en-us/library/system.environment.getenvironmentvariable.aspx)  
  
## <a name="see-also"></a>另請參閱  
 [處理序和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [_putenv、_wputenv](../../c-runtime-library/reference/putenv-wputenv.md)   
 [環境常數](../../c-runtime-library/environmental-constants.md)
