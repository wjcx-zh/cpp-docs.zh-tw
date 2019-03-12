---
title: ___setlc_active_func、___unguarded_readlc_active_add_func
ms.date: 11/04/2016
apiname:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
apilocation:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- ___unguarded_readlc_active_add_func
- ___setlc_active_func
helpviewer_keywords:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
ms.assetid: 605ec4e3-81e5-4ece-935a-f434768cc702
ms.openlocfilehash: 244bb5b0bd6a15dab2de1ad2d6b71c2ae2f850bb
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743986"
---
# <a name="setlcactivefunc-unguardedreadlcactiveaddfunc"></a>___setlc_active_func、___unguarded_readlc_active_add_func

已過時。 CRT 只會為保留二進位相容性匯出這些內部函式。

## <a name="syntax"></a>語法

```cpp
int ___setlc_active_func(void);
int * ___unguarded_readlc_active_add_func(void);
```

## <a name="return-value"></a>傳回值

傳回的值並不重要。

## <a name="remarks"></a>備註

雖然內部 CRT 函式 `___setlc_active_func` 和 `___unguarded_readlc_active_add_func` 已過時且不再提供使用，CRT 程式庫還是會為了保留二進位相容性匯出這些函式。 `___setlc_active_func` 的最初目的是要將目前作用中呼叫數傳回至 `setlocale` 函式。 `___unguarded_readlc_active_add_func` 的最初目的是要在不鎖定地區設定的情況下，傳回參考地區設定的函式數。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`___setlc_active_func`、 `___unguarded_readlc_active_add_func`|none|

## <a name="see-also"></a>另請參閱

[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)
