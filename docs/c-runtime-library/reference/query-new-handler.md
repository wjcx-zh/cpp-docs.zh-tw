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
ms.openlocfilehash: 0cbd434ee0b75f78a2492bd6239bd89f584215ff
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949688"
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

C++ **_Query_new_handler**函數會傳回C++ [_set_new_handler](set-new-handler.md)函數所設定的目前例外狀況處理函式的位址。 如果**new**運算子無法配置記憶體，則會使用 **_set_new_handler**來指定要取得控制的例外狀況處理函式。 如需詳細資訊，請參閱 C++ 語言參考中的 [new 和 delete 運算子](../../cpp/new-and-delete-operators.md)的討論。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_query_new_handler**|\<new.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[free](free.md)<br/>
