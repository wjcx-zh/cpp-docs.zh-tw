---
title: _CrtDoForAllClientObjects | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _CrtDoForAllClientObjects
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
- _CrtDoForAllClientObjects
- CrtDoForAllClientObjects
- crtdbg/_CrdDoForAllClientObjects
dev_langs:
- C++
helpviewer_keywords:
- _CrtDoForAllClientObjects function
- CrtDoForAllClientObjects function
ms.assetid: d0fdb835-3cdc-45f1-9a21-54208e8df248
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 83c555899807c9236b803b0576bc8bf6884fd944
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="crtdoforallclientobjects"></a>_CrtDoForAllClientObjects

應用程式提供的函式呼叫所有 **_CLIENT_BLOCK**堆積 （僅限偵錯版本） 中的型別。

## <a name="syntax"></a>語法

```C
void _CrtDoForAllClientObjects(
   void ( * pfn )( void *, void * ),
   void *context
);
```

### <a name="parameters"></a>參數

*pfn*應用程式提供的函式回呼函式的指標。 此函式的第一個參數指向資料。 第二個參數是傳遞至呼叫的內容指標 **_CrtDoForAllClientObjects**。

*內容*指標傳遞至應用程式提供的函式的應用程式提供的內容。

## <a name="remarks"></a>備註

**_CrtDoForAllClientObjects**函式會搜尋在堆積的連結的清單的記憶體區塊與 **_CLIENT_BLOCK**型別，而且呼叫應用程式提供的函式時此類型的區塊。 找到的區塊和*內容*參數會作為引數傳遞至應用程式提供的函式。 偵錯期間，應用程式可以追蹤特定配置群組，透過明確呼叫偵錯堆積函式以配置記憶體，並指定指派區塊 **_CLIENT_BLOCK**區塊類型。 然後就可以分別追蹤這些區塊，並在遺漏偵測期間和記憶體狀態報告期間個別回報這些區塊。

如果 **_CRTDBG_ALLOC_MEM_DF**的位元欄位[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)旗標未開啟， **_CrtDoForAllClientObjects**立即傳回。 當[_DEBUG](../../c-runtime-library/debug.md)未定義時，呼叫 **_CrtDoForAllClientObjects**會在前置處理期間移除。

如需有關 **_CLIENT_BLOCK**輸入以及如何才能使用其他偵錯函式，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

如果*pfn*是**NULL**、 無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，允許執行[errno、 _doserrno、 _sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)設**EINVAL**並傳回函式。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_CrtDoForAllClientObjects**|\<crtdbg.h>、\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

**程式庫：** 僅限偵錯版的 C 執行階段程式庫。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
[堆積狀態報告函式](/visualstudio/debugger/crt-debug-heap-details)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
