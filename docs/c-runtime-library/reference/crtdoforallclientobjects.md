---
title: _CrtDoForAllClientObjects
ms.date: 11/04/2016
api_name:
- _CrtDoForAllClientObjects
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
- _CrtDoForAllClientObjects
- CrtDoForAllClientObjects
- crtdbg/_CrdDoForAllClientObjects
helpviewer_keywords:
- _CrtDoForAllClientObjects function
- CrtDoForAllClientObjects function
ms.assetid: d0fdb835-3cdc-45f1-9a21-54208e8df248
ms.openlocfilehash: 4626df0db1956efd26ee267cb8cacf8ea4a4570c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942536"
---
# <a name="_crtdoforallclientobjects"></a>_CrtDoForAllClientObjects

針對堆積中的所有 **_CLIENT_BLOCK**類型呼叫應用程式提供的函式（僅限 debug 版本）。

## <a name="syntax"></a>語法

```C
void _CrtDoForAllClientObjects(
   void ( * pfn )( void *, void * ),
   void *context
);
```

### <a name="parameters"></a>參數

*pfn*<br/>
應用程式提供的函式回呼函式的指標。 此函式的第一個參數指向資料。 第二個參數是傳遞至 **_CrtDoForAllClientObjects**呼叫的內容指標。

*context*<br/>
要傳遞至應用程式提供之函式的應用程式提供的內容的指標。

## <a name="remarks"></a>備註

**_CrtDoForAllClientObjects**函數會在堆積的連結清單中搜尋具有 **_CLIENT_BLOCK**類型的記憶體區塊，並在找到此類型的區塊時，呼叫應用程式提供的函式。 找到的區塊和*內容*參數會當做引數傳遞至應用程式提供的函式。 在調試期間，應用程式可以藉由明確呼叫 debug 堆積函式來配置記憶體，並指定要將 **_CLIENT_BLOCK**區塊類型指派給區塊，藉以追蹤特定的配置群組。 然後就可以分別追蹤這些區塊，並在遺漏偵測期間和記憶體狀態報告期間個別回報這些區塊。

如果未開啟[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)旗標的 **_CRTDBG_ALLOC_MEM_DF**位欄位， **_CrtDoForAllClientObjects**會立即傳回。 未定義[_debug](../../c-runtime-library/debug.md)時，會在前置處理期間移除對 **_CrtDoForAllClientObjects**的呼叫。

如需 **_CLIENT_BLOCK**類型以及其他 debug 函數如何使用它的詳細資訊，請參閱[debug 堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

如果*pfn*為**Null**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)會設定為**EINVAL** ，而函式會傳回。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_CrtDoForAllClientObjects**|\<crtdbg.h>、\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

**磁帶**僅限通用 C 執行時間程式庫的 Debug 版本。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
[堆積狀態報告函式](/visualstudio/debugger/crt-debug-heap-details)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
