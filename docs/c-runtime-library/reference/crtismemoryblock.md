---
title: _CrtIsMemoryBlock
ms.date: 11/04/2016
api_name:
- _CrtIsMemoryBlock
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
- CrtlsMemoryBlock
- _CrtIsMemoryBlock
helpviewer_keywords:
- _CrtIsMemoryBlock function
- CrtIsMemoryBlock function
ms.assetid: f7cbbc60-3690-4da0-a07b-68fd7f250273
ms.openlocfilehash: f29745acd06f6f5b3fa96367444e800bdc3e8e3a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938728"
---
# <a name="_crtismemoryblock"></a>_CrtIsMemoryBlock

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
區塊之配置編號的指標，或**為 Null**。

*filename*<br/>
要求區塊或**Null**之原始程式檔名稱的指標。

*linenumber*<br/>
原始程式檔中的行號指標，或為**Null**。

## <a name="return-value"></a>傳回值

如果指定的記憶體區塊位於本機堆積內，而且具有有效的 debug 堆積區塊類型識別碼，則 **_CrtIsMemoryBlock**會傳回**TRUE** ;否則，函數會傳回**FALSE**。

## <a name="remarks"></a>備註

**_CrtIsMemoryBlock**函式會確認指定的記憶體區塊位於應用程式的本機堆積內，而且它具有有效的區塊類型識別碼。 此函式也可用來取得物件配置順序編號，以及原始要求記憶體區塊配置的原始程式檔名/行號。 傳遞*requestNumber*、 *filename*或*linenumber*參數的非**Null**值，會使 **_CrtIsMemoryBlock**將這些參數設定為記憶體區塊的 debug 標頭中的值（如果它在中找到此區塊）本機堆積。 未定義[_debug](../../c-runtime-library/debug.md)時，會在前置處理期間移除對 **_CrtIsMemoryBlock**的呼叫。

如果 **_CrtIsMemoryBlock**失敗，則會傳回**FALSE** ，且輸出參數會初始化為預設值 *： requestNumber*和**lineNumber**會設定為0，而*filename*則設為**Null**。

因為此函式會傳回 **TRUE** 或 **FALSE**，所以可將該函式傳遞至其中一個 [_ASSERT](assert-asserte-assert-expr-macros.md) 巨集，以建立簡單的偵錯處理機制。 如果指定的位址不在本機堆積內，則下列範例會造成判斷提示失敗：

```C
_ASSERTE( _CrtIsMemoryBlock( userData, size, &requestNumber,
          &filename, &linenumber ) );
```

如需 **_CrtIsMemoryBlock**如何搭配其他 debug 函數和宏使用的詳細資訊，請參閱[報告宏](/visualstudio/debugger/macros-for-reporting)。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

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
