---
title: _dupenv_s_dbg、_wdupenv_s_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _dupenv_s_dbg
- _wdupenv_s_dbg
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
- _tdupenv_s_dbg
- _dupenv_s_dbg
- _wdupenv_s_dbg
dev_langs:
- C++
helpviewer_keywords:
- _tdupenv_s_dbg function
- dupenv_s_dbg function
- _wdupenv_s_dbg function
- environment variables
- tdupenv_s_dbg function
- wdupenv_s_dbg function
- _dupenv_s_dbg function
ms.assetid: e3d81148-e24e-46d0-a21d-fd87b5e6256c
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dc6aa566770bd8b2e12cefac22c414fd4c43a118
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="dupenvsdbg-wdupenvsdbg"></a>_dupenv_s_dbg、_wdupenv_s_dbg

從目前環境取得值  這是使用 [_malloc_dbg](malloc-dbg.md) 配置記憶體以提供其他偵錯資訊的 [_dupenv_s、_wdupenv_s](dupenv-s-wdupenv-s.md) 版本。

## <a name="syntax"></a>語法

```C
errno_t _dupenv_s_dbg(
   char **buffer,
   size_t *numberOfElements,
   const char *varname,
   int blockType,
   const char *filename,
   int linenumber
);
errno_t _wdupenv_s_dbg(
   wchar_t **buffer,
   size_t * numberOfElements,
   const wchar_t *varname,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>參數

*buffer*<br/>
要儲存變數的值的緩衝區。

*numberOfElements*<br/>
大小*緩衝區*。

*varname*<br/>
環境變數名稱。

*blockType*<br/>
要求的記憶體區塊類型： **_CLIENT_BLOCK**或 **_NORMAL_BLOCK**。

*filename*<br/>
指標的原始程式檔的名稱或**NULL**。

*linenumber*<br/>
原始程式檔中的行號或**NULL**。

## <a name="return-value"></a>傳回值

若成功，就是零；若失敗，則為錯誤碼。

這些函式會驗證它們的參數;如果*緩衝區*或*varname*是**NULL**，會叫用無效參數處理常式，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，函式會將**errno**至**EINVAL**並傳回**EINVAL**。

若這些函式無法配置足夠的記憶體，這些設定*緩衝區*至**NULL**和*numberOfElements*為 0，並傳回**ENOMEM**。

## <a name="remarks"></a>備註

**_Dupenv_s_dbg**和 **_wdupenv_s_dbg**函式完全相同 **_dupenv_s**和 **_wdupenv_s**不同之處在於，當 **_DEBUG**是定義，這些函式使用的偵錯版本[malloc](malloc.md)， [_malloc_dbg](malloc-dbg.md)、 配置記憶體給環境變數的值。 如需有關偵錯功能的詳細 **_malloc_dbg**，請參閱[_malloc_dbg](malloc-dbg.md)。

在大多數情況中，您不需要明確地呼叫這些函式。 相反地，您可以在其中定義的旗標 **_CRTDBG_MAP_ALLOC**。 當 **_CRTDBG_MAP_ALLOC**定義，但呼叫 **_dupenv_s**和 **_wdupenv_s**重新對應至 **_dupenv_s_dbg**和 **_wdupenv_s_dbg**，分別與*blockType*設 **_NORMAL_BLOCK**。 因此，您不需要明確地呼叫這些函式，除非您想要將做為堆積區塊標示 **_CLIENT_BLOCK**。 如需區塊類型的詳細資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s_dbg**|**_dupenv_s_dbg**|**_dupenv_s_dbg**|**_wdupenv_s_dbg**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_dupenv_s_dbg**|\<crtdbg.h>|
|**_wdupenv_s_dbg**|\<crtdbg.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_dupenv_s_dbg.c
#include  <stdlib.h>
#include <crtdbg.h>

int main( void )
{
   char *pValue;
   size_t len;
   errno_t err = _dupenv_s_dbg( &pValue, &len, "pathext",
      _NORMAL_BLOCK, __FILE__, __LINE__ );
   if ( err ) return -1;
   printf( "pathext = %s\n", pValue );
   free( pValue );
   err = _dupenv_s_dbg( &pValue, &len, "nonexistentvariable",
      _NORMAL_BLOCK, __FILE__, __LINE__ );
   if ( err ) return -1;
   printf( "nonexistentvariable = %s\n", pValue );
   free( pValue ); // It's OK to call free with NULL
}
```

```Output
pathext = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.pl
nonexistentvariable = (null)
```

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[環境常數](../../c-runtime-library/environmental-constants.md)<br/>
[getenv_s、_wgetenv_s](getenv-s-wgetenv-s.md)<br/>
[_putenv_s、_wputenv_s](putenv-s-wputenv-s.md)<br/>
