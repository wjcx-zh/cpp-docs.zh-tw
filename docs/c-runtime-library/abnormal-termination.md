---
title: _abnormal_termination
ms.date: 11/04/2016
api_name:
- _abnormal_termination
api_location:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _abnormal_termination
helpviewer_keywords:
- _abnormal_termination
ms.assetid: 952970a4-9586-4c3d-807a-db729448c91c
ms.openlocfilehash: a963f1059eccaddce9ec01cd53a07df668ee46c6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213654"
---
# <a name="_abnormal_termination"></a>_abnormal_termination

指出 **`__finally`** 當系統執行終止處理常式的內部清單時，是否輸入[try-catch 語句](../cpp/try-finally-statement.md)的區塊。

## <a name="syntax"></a>語法

```cpp
int   _abnormal_termination(
   );
```

## <a name="return-value"></a>傳回值

**`true`** 如果*系統正在回溯堆疊，則*為，否則為 **`false`** 。

## <a name="remarks"></a>備註

這是用來管理回溯例外狀況的內部函式，不是從使用者程式碼呼叫。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|_abnormal_termination|excpt.h|

## <a name="see-also"></a>另請參閱

[try-finally 語句](../cpp/try-finally-statement.md)
