---
title: _strdup_dbg、_wcsdup_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _strdup_dbg
- _wcsdup_dbg
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
- _wcsdup_dbg
- strdup_dbg
- _strdup_dbg
- wcsdup_dbg
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b6e8f5f4634ec93cab619c1e073fa8071691fe6
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
---
# <a name="strdupdbg-wcsdupdbg"></a>_strdup_dbg、_wcsdup_dbg

新版[_strdup and _wcsdup](strdup-wcsdup-mbsdup.md)所使用的偵錯版本**malloc**。

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
要求配置作業的來源檔案名稱的指標或**NULL**。

*linenumber*<br/>
其中要求配置作業之原始程式檔中的行號或**NULL**。

## <a name="return-value"></a>傳回值

所有這些函式會傳回所複製字串的儲存位置的指標或**NULL**無法配置儲存區時。

## <a name="remarks"></a>備註

**_Strdup_dbg**和 **_wcsdup_dbg**函式完全相同 **_strdup**和 **_wcsdup**不同之處在於，當 **_偵錯**是定義，這些函式使用的偵錯版本**malloc**， **_malloc_dbg**、 所複製字串配置記憶體。 如需有關偵錯功能的詳細 **_malloc_dbg**，請參閱[_malloc_dbg](malloc-dbg.md)。

在大多數情況中，您不需要明確地呼叫這些函式。 相反地，您可以在其中定義的旗標 **_CRTDBG_MAP_ALLOC**。 當 **_CRTDBG_MAP_ALLOC**定義，但呼叫 **_strdup**和 **_wcsdup**重新對應至 **_strdup_dbg**和 **_wcsdup_dbg**，分別與*blockType*設 **_NORMAL_BLOCK**。 因此，您不需要明確地呼叫這些函式，除非您想要將做為堆積區塊標示 **_CLIENT_BLOCK**。 如需區塊類型的詳細資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsdup_dbg**|**_strdup_dbg**|**_mbsdup**|**_wcsdup_dbg**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_strdup_dbg**， **_wcsdup_dbg**|\<crtdbg.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strdup、_wcsdup、_mbsdup](strdup-wcsdup-mbsdup.md)<br/>
[堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
