---
title: _fullpath_dbg、_wfullpath_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _wfullpath_dbg
- _fullpath_dbg
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
- wfullpath_dbg
- _wfullpath_dbg
- _fullpath_dbg
- fullpath_dbg
dev_langs:
- C++
helpviewer_keywords:
- _fullpath_dbg function
- relative file paths
- absolute paths
- fullpath_dbg function
- _wfullpath_dbg function
- wfullpath_dbg function
ms.assetid: 81f72f85-07da-4f5c-866a-598e0fb03f6b
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c94001008cbe10fa9dcc3ceaca8c5b48cea0c2d0
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="fullpathdbg-wfullpathdbg"></a>_fullpath_dbg、_wfullpath_dbg

新版[_fullpath、 _wfullpath](fullpath-wfullpath.md)所使用的偵錯版本**malloc**配置記憶體。

## <a name="syntax"></a>語法

```C
char *_fullpath_dbg(
   char *absPath,
   const char *relPath,
   size_t maxLength,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wfullpath_dbg(
   wchar_t *absPath,
   const wchar_t *relPath,
   size_t maxLength,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>參數

*absPath*<br/>
包含絕對路徑或完整路徑名稱之緩衝區的指標或**NULL**。

*relPath*<br/>
相對路徑名稱。

*maxLength*<br/>
絕對路徑名稱緩衝區的最大長度 (*absPath*)。 這個長度是以位元組為單位的 **_fullpath**但寬字元 (**wchar_t**) 的 **_wfullpath**。

*blockType*<br/>
要求的記憶體區塊類型： **_CLIENT_BLOCK**或 **_NORMAL_BLOCK**。

*filename*<br/>
要求配置作業之原始程式檔名稱的指標或**NULL**。

*linenumber*<br/>
其中要求配置作業，原始程式檔中的行號或**NULL**。

## <a name="return-value"></a>傳回值

每個函式會傳回包含絕對路徑名稱之緩衝區的指標 (*absPath*)。 如果發生錯誤 (例如，如果的值傳遞*relPath*包含無效或找不到的磁碟機代號或建立的絕對路徑名稱的長度 (*absPath*) 大於*maxLength*) 函式會傳回**NULL**。

## <a name="remarks"></a>備註

**_Fullpath_dbg**和 **_wfullpath_dbg**函式完全相同 **_fullpath**和 **_wfullpath**不同之處在於，當 **_DEBUG**是定義，這些函式使用的偵錯版本**malloc**， **_malloc_dbg**來配置記憶體，如果 NULL 當做第一個參數傳遞。 如需有關偵錯功能的詳細 **_malloc_dbg**，請參閱[_malloc_dbg](malloc-dbg.md)。

在大多數情況中，您不需要明確地呼叫這些函式。 相反地，您可以定義 **_CRTDBG_MAP_ALLOC**旗標。 當 **_CRTDBG_MAP_ALLOC**定義，但呼叫 **_fullpath**和 **_wfullpath**重新對應至 **_fullpath_dbg**和 **_wfullpath_dbg**，分別與*blockType*設 **_NORMAL_BLOCK**。 因此，您不需要明確地呼叫這些函式，除非您想要將做為堆積區塊標示 **_CLIENT_BLOCK**。 如需詳細資訊，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath_dbg**|**_fullpath_dbg**|**_fullpath_dbg**|**_wfullpath_dbg**|

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**_fullpath_dbg**|\<crtdbg.h>|
|**_wfullpath_dbg**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[_fullpath、_wfullpath](fullpath-wfullpath.md)<br/>
[堆積配置函式的偵錯版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
