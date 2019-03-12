---
title: _execute_onexit_table、_initialize_onexit_table、_register_onexit_function
ms.date: 11/04/2016
apiname:
- _execute_onexit_table
- _initialize_onexit_table
- _register_onexit_function
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _execute_onexit_table
- process/_execute_onexit_table
- _initialize_onexit_table
- process/_initialize_onexit_table
- _register_onexit_function
- process/_register_onexit_function
helpviewer_keywords:
- _execute_onexit_table function
- _initialize_onexit_table function
- _register_onexit_function function
ms.assetid: ad9e4149-d4ad-4fdf-aaaf-cf786fcb4473
ms.openlocfilehash: 0090d5d1504f4320c122ae1e811e0af88cccdd2e
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741637"
---
# <a name="executeonexittable-initializeonexittable-registeronexitfunction"></a>_execute_onexit_table、_initialize_onexit_table、_register_onexit_function

管理要在結束時呼叫的常式。

## <a name="syntax"></a>語法

```
int _initialize_onexit_table(
    _onexit_table_t* table
    );

int _register_onexit_function(
    _onexit_table_t* table,
    _onexit_t        function
    );

int _execute_onexit_table(
    _onexit_table_t* table
    );
```

#### <a name="parameters"></a>參數

*table*<br/>
[in, out] onexit 函式表的指標。

*function*<br/>
[in] 要新增至 onexit 函式表中的函式指標。

## <a name="return-value"></a>傳回值

如果成功，則傳回 0。 否則，傳回負值。

## <a name="remarks"></a>備註

這些函式是用來支援 C 執行階段的基礎結構實作詳細資料，不應該直接從程式碼呼叫。 C 執行階段使用 *onexit 函式表*來代表按 `atexit`、`at_quick_exit` 和 `_onexit` 呼叫登錄的函式順序。 Onexit 函式表資料結構是不透明的 C 執行階段實作詳細資料，其資料成員的順序和意義可能會變更。 它們不該由外部程式碼檢查。

`_initialize_onexit_table` 函式會將 onexit 函式表初始化為其初始值。  必須先呼叫此函式，再將 onexit 函式表傳遞至 `_register_onexit_function` 或 `_execute_onexit_table`。

`_register_onexit_function` 函式會將某個函式附加至 onexit 函式表的結尾。

`_execute_onexit_table` 函式會執行 onexit 函式表中所有的函式、清除資料表，然後傳回。 呼叫 `_execute_onexit_table` 之後，資料表即為非有效狀態，必須先呼叫 `_initialize_onexit_table` 重新初始化才能再次使用資料表。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`_initialize_onexit_table function`, `_register_onexit_function`, `_execute_onexit_table`|\<process.h>|

`_initialize_onexit_table`、`_register_onexit_function` 與 `_execute_onexit_table` 函式為 Microsoft 特定的。 如需相容性資訊，請參閱 [相容性](../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[atexit](../c-runtime-library/reference/atexit.md)<br/>
[exit、_Exit、_exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_onexit、_onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)
