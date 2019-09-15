---
title: _strdup_dbg、_wcsdup_dbg
ms.date: 11/04/2016
api_name:
- _strdup_dbg
- _wcsdup_dbg
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
- _wcsdup_dbg
- strdup_dbg
- _strdup_dbg
- wcsdup_dbg
helpviewer_keywords:
- _wcsdup_dbg function
- stdup_dbg function
- copying strings
- duplicating strings
- strings [C++], copying
- strings [C++], duplicating
- _strdup_dbg function
- wcsdup_dbg function
ms.assetid: 681db70c-d124-43ab-b83e-5eeea9035097
ms.openlocfilehash: 9f7d4fd8781269ee37f7515fdcab72e5195fdf00
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958193"
---
# <a name="_strdup_dbg-_wcsdup_dbg"></a>_strdup_dbg、_wcsdup_dbg

使用「 **malloc**的偵錯工具」版本的[_strdup 和 _wcsdup](strdup-wcsdup-mbsdup.md)版本。

## <a name="syntax"></a>語法

```C
char *_strdup_dbg(
   const char *strSource,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wcsdup_dbg(
   const wchar_t *strSource,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>參數

*strSource*<br/>
以 Null 結束的來源字串。

*blockType*<br/>
要求的記憶體區塊類型： **_CLIENT_BLOCK**或 **_NORMAL_BLOCK**。

*filename*<br/>
要求配置作業之原始程式檔的名稱的指標，或為**Null**。

*linenumber*<br/>
原始程式檔中的行號，其中要求配置作業，或**為 Null**。

## <a name="return-value"></a>傳回值

所有這些函式都會傳回所複製字串之儲存位置的指標，如果無法配置儲存區，則傳回**Null** 。

## <a name="remarks"></a>備註

**_Strdup_dbg**和 **_wcsdup_dbg**函式與 **_strdup**和 **_wcsdup**相同，不同之處在于，當已定義 **_debug**時，這些函式會使用對**malloc**、 **_malloc_dbg**的 DEBUG 版本來配置複製字串的記憶體。 如需 **_malloc_dbg**之偵錯工具功能的詳細資訊，請參閱[_malloc_dbg](malloc-dbg.md)。

在大多數情況中，您不需要明確地呼叫這些函式。 相反地，您可以定義旗標 **_CRTDBG_MAP_ALLOC**。 當定義 **_CRTDBG_MAP_ALLOC**時， **_strdup**和 **_wcsdup**的呼叫會分別重新對應至 **_strdup_dbg**和 **_wcsdup_dbg**，並將*blockType*設定為 **_NORMAL_BLOCK**。 因此，您不需要明確呼叫這些函式，除非您想要將堆積區塊標記為 **_CLIENT_BLOCK**。 如需區塊類型的詳細資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsdup_dbg**|**_strdup_dbg**|**_mbsdup**|**_wcsdup_dbg**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_strdup_dbg**、 **_wcsdup_dbg**|\<crtdbg.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strdup、_wcsdup、_mbsdup](strdup-wcsdup-mbsdup.md)<br/>
[堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
