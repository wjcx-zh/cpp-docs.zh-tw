---
title: _query_new_mode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _query_new_mode
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- query_new_mode
- _query_new_mode
dev_langs:
- C++
helpviewer_keywords:
- query_new_mode function
- handler modes
- _query_new_mode function
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8907b043e8b4441d6e5213a1d386dbc1a5a6910a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="querynewmode"></a>_query_new_mode

傳回一個整數，表示新的處理常式模式所設定 **_set_new_mode**如**malloc**。

## <a name="syntax"></a>語法

```C
int _query_new_mode(
   void
);
```

## <a name="return-value"></a>傳回值

傳回目前新處理常式的模式，也就是 0 或 1， **malloc**。 傳回值為 1，表示無法配置記憶體， **malloc**呼叫新的處理常式; 傳回值 0 表示，不會。

## <a name="remarks"></a>備註

C + + **_query_new_mode**函式會傳回一個整數，表示新的處理常式模式所設定的 c + + [_set_new_mode](set-new-mode.md)函式[malloc](malloc.md)。 新的處理常式模式指出是否在無法配置記憶體， **malloc**是新的處理常式呼叫所設定的[_set_new_handler](set-new-handler.md)。 根據預設， **malloc**不會將新的處理常式呼叫失敗。 您可以使用 **_set_new_mode**因此覆寫這個行為的失敗**malloc**呼叫新的處理常式在相同的方式來**新**運算子會在無法時配置的記憶體。 如需詳細資訊，請參閱 C++ 語言參考中的 [new 和 delete 運算子](../../cpp/new-and-delete-operators.md)的討論。

## <a name="requirements"></a>需求

|常式|必要的標頭|
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
