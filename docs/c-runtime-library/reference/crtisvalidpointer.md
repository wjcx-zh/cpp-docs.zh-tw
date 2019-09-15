---
title: _CrtIsValidPointer
ms.date: 11/04/2016
api_name:
- _CrtIsValidPointer
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
- CrtlsValidPointer
- _CrtIsValidPointer
helpviewer_keywords:
- CrtIsValidPointer function
- _CrtIsValidPointer function
ms.assetid: 91c35590-ea5e-450f-a15d-ad8d62ade1fa
ms.openlocfilehash: 490d2dea097935dee2cd2a003aa28e32f1ced69d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938775"
---
# <a name="_crtisvalidpointer"></a>_CrtIsValidPointer

驗證指標不是 null。 在 Visual Studio 2010 之前的 C 執行階段程式庫版本中，驗證指定的記憶體範圍是否可有效用於讀取和寫入 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
int _CrtIsValidPointer(
   const void *address,
   unsigned int size,
   int access
);
```

### <a name="parameters"></a>參數

*address*<br/>
要測試有效性之記憶體的開頭的指標。

*size*<br/>
指定之記憶體範圍的大小 (位元組)。

*access*<br/>
決定記憶體範圍的讀取/寫入存取範圍。

## <a name="return-value"></a>傳回值

如果指定的指標不是 null， **_CrtIsValidPointer**會傳回 TRUE。 在 Visual Studio 2010 之前的 C 執行階段程式庫版本中，若記憶體範圍可有效供指定的一或多個作業使用，則會傳回 TRUE。 否則，此函式會傳回 FALSE。

## <a name="remarks"></a>備註

從 Visual Studio 2010 中的 CRT 程式庫開始，會忽略*大小*和*存取*參數，而且 **_CrtIsValidPointer**只會驗證指定的*位址*是否不是 null。 因為這項測試很容易由您自行執行，所以我們不建議您使用此函式。 在 Visual Studio 2010 之前的版本中，函式會確認從*位址*開始，以及針對*大小*位元組擴充的記憶體範圍，對指定的協助工具作業或操作而言是有效的。 當*access*設定為 TRUE 時，會驗證記憶體範圍以進行讀取和寫入。 當*存取*為 FALSE 時，只會驗證記憶體範圍以進行讀取。 未定義[_debug](../../c-runtime-library/debug.md)時，會在前置處理期間移除對 **_CrtIsValidPointer**的呼叫。

因為此函式會傳回 TRUE 或 FALSE，所以可將該函式傳遞至其中一個 [_ASSERT](assert-asserte-assert-expr-macros.md) 巨集，以建立簡單的偵錯處理機制。 若記憶體範圍無法有效用於讀取和寫入作業，則下列範例會引發判斷提示：

```C
_ASSERTE( _CrtIsValidPointer( address, size, TRUE ) );
```

如需 **_CrtIsValidPointer**如何搭配其他 debug 函數和宏使用的詳細資訊，請參閱[報告宏](/visualstudio/debugger/macros-for-reporting)。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_CrtIsValidPointer**|\<crtdbg.h>|

**_CrtIsValidPointer**是 Microsoft 擴充功能。 如需相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

請參閱 [_CrtIsValidHeapPointer](crtisvalidheappointer.md) 主題的範例。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
