---
title: _getpid
description: _Getpid 的 API 參考，可取得進程識別。
ms.date: 11/04/2016
api_name:
- _getpid
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getpid
helpviewer_keywords:
- getpid function
- _getpid function
- process identification numbers
ms.assetid: d3e13bae-9a0c-4f33-86d3-ec9df9519285
ms.openlocfilehash: fc2de8e0b6e87d04bd9ae29ce3a945c048af00e2
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556485"
---
# <a name="_getpid"></a>_getpid

取得處理序識別碼。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _getpid( void );
```

## <a name="return-value"></a>傳回值

傳回從系統取得的處理序 ID。 不會傳回錯誤。

## <a name="remarks"></a>備註

**_Getpid**函式會從系統取得處理序識別碼。 處理序 ID 可唯一識別呼叫處理序。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_getpid**|\<process.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_getpid.c
// This program uses _getpid to obtain
// the process ID and then prints the ID.

#include <stdio.h>
#include <process.h>

int main( void )
{
   // If run from command line, shows different ID for
   // command line than for operating system shell.

   printf( "Process id: %d\n", _getpid() );
}
```

```Output
Process id: 3584
```

## <a name="see-also"></a>另請參閱

[流程式控制制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_mktemp、_wmktemp](mktemp-wmktemp.md)<br/>
