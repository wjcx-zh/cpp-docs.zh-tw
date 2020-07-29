---
title: _query_new_mode
ms.date: 11/04/2016
api_name:
- _query_new_mode
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
- query_new_mode
- _query_new_mode
helpviewer_keywords:
- query_new_mode function
- handler modes
- _query_new_mode function
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
ms.openlocfilehash: 26fabc71337f1554b63909697b601a0bd9e86638
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216826"
---
# <a name="_query_new_mode"></a>_query_new_mode

傳回整數，指出 **_set_new_mode**為**malloc**所設定的新處理常式模式。

## <a name="syntax"></a>語法

```C
int _query_new_mode(
   void
);
```

## <a name="return-value"></a>傳回值

傳回**malloc**的目前新處理常式模式，亦即0或1。 傳回值1表示在無法配置記憶體時， **malloc**會呼叫新的處理常式常式;傳回值為0時，表示它不是。

## <a name="remarks"></a>備註

C + + **_query_new_mode**函式會傳回一個整數，表示新的處理常式模式，它會針對[Malloc](malloc.md)的 c + + [_set_new_mode](set-new-mode.md)函數所設定。 新的處理常式模式指出，在無法配置記憶體時， **malloc**是否會呼叫[_set_new_handler](set-new-handler.md)所設定的新處理常式常式。 根據預設， **malloc**不會在失敗時呼叫新的處理常式常式。 您可以使用 **_set_new_mode**來覆寫此行為，如此一來，當失敗**malloc**呼叫新的處理常式常式時，其方式會與 **`new`** 運算子無法配置記憶體時相同。 如需詳細資訊，請參閱 C++ 語言參考中的 [new 和 delete 運算子](../../cpp/new-and-delete-operators.md)的討論。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_query_new_mode**|\<new.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[受](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
