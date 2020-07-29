---
title: _query_new_handler
ms.date: 11/04/2016
api_name:
- _query_new_handler
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
- api-ms-win-crt-heap-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _query_new_handler
- query_new_handler
helpviewer_keywords:
- query_new_handler function
- handler routines
- error handling
- _query_new_handler function
ms.assetid: 9a84b5c3-fe33-4c01-83a0-be87dc3ec518
ms.openlocfilehash: 9c87a63a9ed94eb1473230aedb5e9c17fcc6410b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216839"
---
# <a name="_query_new_handler"></a>_query_new_handler

傳回目前新處理常式的位址。

## <a name="syntax"></a>語法

```C
_PNH _query_new_handler(
   void
);
```

## <a name="return-value"></a>傳回值

傳回 **_set_new_handler**所設定之目前新處理常式常式的位址。

## <a name="remarks"></a>備註

C + + **_query_new_handler**函式會傳回 c + + [_set_new_handler](set-new-handler.md)函數所設定的目前例外狀況處理函式的位址。 **_set_new_handler**如果 **`new`** 運算子無法配置記憶體，則會使用 _set_new_handler 來指定要取得控制的例外狀況處理函數。 如需詳細資訊，請參閱 C++ 語言參考中的 [new 和 delete 運算子](../../cpp/new-and-delete-operators.md)的討論。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_query_new_handler**|\<new.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[受](free.md)<br/>
