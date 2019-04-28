---
title: _CrtIsMemoryBlock
ms.date: 11/04/2016
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
helpviewer_keywords:
- _CrtIsMemoryBlock function
- CrtIsMemoryBlock function
ms.assetid: f7cbbc60-3690-4da0-a07b-68fd7f250273
ms.openlocfilehash: c4a85ebeb45552c6f5355853de2a45766d6bc984
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339893"
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

*userData*<br/>
要確認之記憶體區塊開頭的指標。

*size*<br/>
指定區塊的大小 (以位元組為單位)。

*requestNumber*<br/>
配置數區塊的指標或**NULL**。

*filename*<br/>
要求區塊之原始程式檔名稱的指標或**NULL**。

*linenumber*<br/>
原始程式檔中的行號的指標或**NULL**。

## <a name="return-value"></a>傳回值

**_CrtIsMemoryBlock**會傳回 **，則為 TRUE**如果指定的記憶體區塊位於本機堆積，且具有有效的偵錯堆積區塊類型識別項; 否則函式會傳回**FALSE**。

## <a name="remarks"></a>備註

**_CrtIsMemoryBlock**函式會確認指定的記憶體區塊位於應用程式的本機堆積內，且具有有效的區塊類型識別項。 此函式也可用來取得物件配置順序編號，以及原始要求記憶體區塊配置的原始程式檔名/行號。 傳遞非**NULL**值*requestNumber*，*檔名*，或*linenumber*參數原因 **_CrtIsMemoryBlock**將這些參數設定為記憶體區塊偵錯標頭中的值，如果在本機堆積中找到此區塊。 當[_DEBUG](../../c-runtime-library/debug.md)未定義，呼叫 **_CrtIsMemoryBlock**會在前置處理期間移除。

如果 **_CrtIsMemoryBlock**失敗，則會傳回**FALSE**且輸出參數會初始化為預設值： *requestNumber*並**lineNumber**會設定為 0 並*檔名*設定為**NULL**。

因為此函式會傳回 **TRUE** 或 **FALSE**，所以可將該函式傳遞至其中一個 [_ASSERT](assert-asserte-assert-expr-macros.md) 巨集，以建立簡單的偵錯處理機制。 如果指定的位址不在本機堆積內，則下列範例會造成判斷提示失敗：

```C
_ASSERTE( _CrtIsMemoryBlock( userData, size, &requestNumber,
          &filename, &linenumber ) );
```

如需有關如何 **_CrtIsMemoryBlock**可以搭配其他偵錯函式和巨集，請參閱[報告巨集](/visualstudio/debugger/macros-for-reporting)。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_CrtIsMemoryBlock**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

請參閱 [_CrtIsValidHeapPointer](crtisvalidheappointer.md) 主題的範例。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
