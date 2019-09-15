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
ms.openlocfilehash: 59724dafdc6488596478d0b44b254c4f498fce99
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950106"
---
# <a name="_query_new_mode"></a>_query_new_mode

傳回一個整數，表示 **_set_new_mode**針對**malloc**所設定的新處理常式模式。

## <a name="syntax"></a>語法

```C
int _query_new_mode(
   void
);
```

## <a name="return-value"></a>傳回值

傳回**malloc**的目前新處理常式模式，亦即0或1。 傳回值1表示在無法配置記憶體時， **malloc**會呼叫新的處理常式常式;傳回值為0時，表示它不是。

## <a name="remarks"></a>備註

C++ **_Query_new_mode**函式會傳回整數，指出C++ [_set_new_mode](set-new-mode.md)函數針對[malloc](malloc.md)所設定的新處理常式模式。 新的處理常式模式指出，在無法配置記憶體時， **malloc**是否會呼叫[_set_new_handler](set-new-handler.md)所設定的新處理常式常式。 根據預設， **malloc**不會在失敗時呼叫新的處理常式常式。 您可以使用 **_set_new_mode**來覆寫此行為，如此一來，當失敗**malloc**呼叫新的處理常式常式時，就會以**新**的運算子無法配置記憶體的方式執行。 如需詳細資訊，請參閱 C++ 語言參考中的 [new 和 delete 運算子](../../cpp/new-and-delete-operators.md)的討論。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_query_new_mode**|\<new.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
