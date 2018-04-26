---
title: _CrtIsMemoryBlock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _CrtIsMemoryBlock
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
- CrtlsMemoryBlock
- _CrtIsMemoryBlock
dev_langs:
- C++
helpviewer_keywords:
- _CrtIsMemoryBlock function
- CrtIsMemoryBlock function
ms.assetid: f7cbbc60-3690-4da0-a07b-68fd7f250273
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a556ef0ade8e336efaca64b79c86c41cc9643c9a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="crtismemoryblock"></a>_CrtIsMemoryBlock

確認指定的記憶體區塊位於本機堆積，且具有有效的偵錯堆積區塊類型識別項 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
int _CrtIsMemoryBlock(
   const void *userData,
   unsigned int size,
   long *requestNumber,
   char **filename,
   int *linenumber
);
```

### <a name="parameters"></a>參數

*UserData*<br/>
要確認之記憶體區塊開頭的指標。

*size*<br/>
指定區塊的大小 (以位元組為單位)。

*requestNumber*<br/>
在區塊的配置編號的指標或**NULL**。

*filename*<br/>
要求區塊的來源檔案名稱的指標或**NULL**。

*linenumber*<br/>
原始程式檔中的行號的指標或**NULL**。

## <a name="return-value"></a>傳回值

**_CrtIsMemoryBlock**傳回**TRUE**如果指定的記憶體區塊是位在本機堆積內，而且具有有效的偵錯堆積區塊類型識別項; 否則函數會傳回**FALSE**。

## <a name="remarks"></a>備註

**_CrtIsMemoryBlock**函式會驗證指定的記憶體區塊會位於應用程式的本機堆積內，而且它有無效的區塊類型識別項。 此函式也可用來取得物件配置順序編號，以及原始要求記憶體區塊配置的原始程式檔名/行號。 傳遞非 NULL 值，以進行*requestNumber*， *filename*，或*linenumber*參數原因 **_CrtIsMemoryBlock**設定這些參數，以記憶體區塊中的值來進行偵錯標頭，在本機堆積中找到的區塊。 當[_DEBUG](../../c-runtime-library/debug.md)未定義時，呼叫 **_CrtIsMemoryBlock**會在前置處理期間移除。

如果 **_CrtIsMemoryBlock**失敗，它會傳回**FALSE**和輸出參數會初始化為預設值： *requestNumber*和**lineNumber**設為 0 和*filename*設**NULL**。

因為此函式會傳回 **TRUE** 或 **FALSE**，所以可將該函式傳遞至其中一個 [_ASSERT](assert-asserte-assert-expr-macros.md) 巨集，以建立簡單的偵錯處理機制。 如果指定的位址不在本機堆積內，則下列範例會造成判斷提示失敗：

```C
_ASSERTE( _CrtIsMemoryBlock( userData, size, &requestNumber,
          &filename, &linenumber ) );
```

如需有關如何 **_CrtIsMemoryBlock**可以搭配其他偵錯函式和巨集，請參閱[報告巨集](/visualstudio/debugger/macros-for-reporting)。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_CrtIsMemoryBlock**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

請參閱 [_CrtIsValidHeapPointer](crtisvalidheappointer.md) 主題的範例。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
