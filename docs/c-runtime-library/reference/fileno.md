---
title: _fileno
description: _Fileno 的 API 參考;，可取得與資料流程相關聯的檔案描述項。
ms.date: 4/2/2020
api_name:
- _fileno
- _o__fileno
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fileno
helpviewer_keywords:
- file handles [C++], getting from streams
- fileno function
- _fileno function
- streams, getting file handles
ms.assetid: 86474174-2f17-4100-bcc4-352dd976c7b5
ms.openlocfilehash: c07f446cc3c5c29fb102a74b2b095957589eab46
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89554847"
---
# <a name="_fileno"></a>_fileno

取得與資料流相關聯的檔案描述項。

## <a name="syntax"></a>語法

```C
int _fileno(
   FILE *stream
);
```

### <a name="parameters"></a>參數

*流*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

**_fileno** 會傳回檔案描述項。 不會傳回錯誤。 如果 *資料流程* 未指定開啟的檔案，則結果為未定義。 如果資料流程為 **Null**， **_fileno** 會叫用不正確參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，此函式會傳回 -1，並將 **errno** 設為 **EINVAL**。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

> [!NOTE]
> 如果 **stdout** 或 **stderr** 沒有與輸出資料流程相關聯 (例如，在沒有主控台視窗的 Windows 應用程式中) ，傳回的檔案描述元是-2。 在舊版本中，傳回的檔案描述元是 -1。 此變更可讓應用程式區分這個條件與錯誤。

## <a name="remarks"></a>備註

**_Fileno**常式會傳回目前與*資料流程*相關聯的檔案描述項。 此常式可當作函式和巨集來實作。 如需選擇其中一個實作的資訊，請參閱[選擇函式與巨集](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|函式|必要的標頭|
|--------------|---------------------|
|**_fileno**|\<stdio.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_fileno.c
// This program uses _fileno to obtain
// the file descriptor for some standard C streams.
//

#include <stdio.h>

int main( void )
{
   printf( "The file descriptor for stdin is %d\n", _fileno( stdin ) );
   printf( "The file descriptor for stdout is %d\n", _fileno( stdout ) );
   printf( "The file descriptor for stderr is %d\n", _fileno( stderr ) );
}
```

```Output
The file descriptor for stdin is 0
The file descriptor for stdout is 1
The file descriptor for stderr is 2
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_fdopen、_wfdopen](fdopen-wfdopen.md)<br/>
[_filelength、_filelengthi64](filelength-filelengthi64.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[freopen、_wfreopen](freopen-wfreopen.md)<br/>
