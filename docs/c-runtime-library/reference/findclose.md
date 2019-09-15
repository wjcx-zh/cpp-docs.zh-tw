---
title: _findclose
ms.date: 11/04/2016
api_name:
- _findclose
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
- api-ms-win-crt-filesystem-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _findclose
- findclose
helpviewer_keywords:
- _findclose function
- findclose function
ms.assetid: 9216c573-0878-444c-b5d7-cdaf16fb9163
ms.openlocfilehash: c67336cc12bcdee754edd40b91078faa83a17984
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957326"
---
# <a name="_findclose"></a>_findclose

關閉指定的搜尋控制代碼，並釋出相關聯的資源。

## <a name="syntax"></a>語法

```C
int _findclose(
   intptr_t handle
);
```

### <a name="parameters"></a>參數

*圖*<br/>
先前呼叫 **_findfirst**所傳回的搜尋控制碼。

## <a name="return-value"></a>傳回值

如果成功， **_findclose**會傳回0。 否則，它會傳回-1，並將**errno**設定為**ENOENT**，這表示找不到任何相符的檔案。

## <a name="requirements"></a>需求

|函數|必要的標頭|
|--------------|---------------------|
|**_findclose**|\<io.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[系統呼叫](../../c-runtime-library/system-calls.md)<br/>
[檔案名稱搜尋函式](../../c-runtime-library/filename-search-functions.md)<br/>
