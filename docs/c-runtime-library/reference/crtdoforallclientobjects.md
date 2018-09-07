---
title: _CrtDoForAllClientObjects | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 378ef3c6218d1f57cd1d817d8895b3ff8b081ecb
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105337"
---
# <a name="crtdoforallclientobjects"></a>_CrtDoForAllClientObjects

所有呼叫的應用程式所提供的函式 **_CLIENT_BLOCK**堆積 （僅限偵錯版本） 中的類型。

## <a name="syntax"></a>語法

```C
void _CrtDoForAllClientObjects(
   void ( * pfn )( void *, void * ),
   void *context
);
```

### <a name="parameters"></a>參數

*pfn*<br/>
應用程式提供的函式回呼函式的指標。 此函式的第一個參數指向資料。 第二個參數是傳遞至呼叫的內容指標 **_CrtDoForAllClientObjects**。

*context*<br/>
要傳遞至應用程式提供之函式的應用程式提供的內容的指標。

## <a name="remarks"></a>備註

**_CrtDoForAllClientObjects**函式會搜尋使用的記憶體區塊的堆積的連結的串列 **_CLIENT_BLOCK**類型和呼叫應用程式提供的函式的這種類型的區塊時找到。 找到的區塊並*內容*參數做為引數傳遞至應用程式提供的函式。 偵錯期間，應用程式可以藉由明確呼叫偵錯堆積函式配置的記憶體，並指定區塊，被指派追蹤特定群組的配置 **_CLIENT_BLOCK**區塊類型。 然後就可以分別追蹤這些區塊，並在遺漏偵測期間和記憶體狀態報告期間個別回報這些區塊。

如果 **_CRTDBG_ALLOC_MEM_DF**位元欄位[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)旗標未開啟， **_CrtDoForAllClientObjects**立即傳回。 當[_DEBUG](../../c-runtime-library/debug.md)未定義，呼叫 **_CrtDoForAllClientObjects**會在前置處理期間移除。

如需詳細資訊 **_CLIENT_BLOCK**輸入，它可以如何使用其他偵錯函式，請參閱[偵錯堆積上的區塊類型](/visualstudio/debugger/crt-debug-heap-details)。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

如果*pfn*是**NULL**，無效參數處理常式會叫用，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續，請執行[errno、 _doserrno、 _sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)設為**EINVAL** ，函式傳回。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_CrtDoForAllClientObjects**|\<crtdbg.h>、\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

**程式庫：** 僅限偵錯版的 C 執行階段程式庫。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
[堆積狀態報告函式](/visualstudio/debugger/crt-debug-heap-details)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
