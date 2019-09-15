---
title: _initterm、_initterm_e
ms.date: 11/04/2016
api_name:
- _initterm_e
- _initterm
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _initterm_e
- initterm
- _initterm
- initterm_e
helpviewer_keywords:
- initterm function
- initterm_e function
- _initterm function
- _initterm_e function
ms.assetid: 85131efe-c747-429a-8897-bcdedb000172
ms.openlocfilehash: 7e85494bf6c8215d03602ee112e1ff2c0f1cf6f2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954622"
---
# <a name="_initterm-_initterm_e"></a>_initterm、_initterm_e

查核函式指標的資料表，並將它們初始化的內部方法。

第一個指標是在資料表中的起始位置，而第二個指標是結束位置。

## <a name="syntax"></a>語法

```C
void __cdecl _initterm(
   PVFV *,
   PVFV *
);

int __cdecl _initterm_e(
   PVFV *,
   PVFV *
);
```

## <a name="return-value"></a>傳回值

如果初始化失敗並擲回錯誤，則傳回非零錯誤碼；若未發生錯誤則為 0。

## <a name="remarks"></a>備註

這些方法只會在 C++ 程式初始化期間由內部呼叫。 請勿在程式中呼叫這些方法。

當這些方法引導資料表的函式專案時，它們會略過**Null**專案並繼續。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
