---
title: _execute_onexit_table、_initialize_onexit_table、_register_onexit_function
ms.date: 4/2/2020
api_name:
- _execute_onexit_table
- _initialize_onexit_table
- _register_onexit_function
- _o__execute_onexit_table
- _o__initialize_onexit_table
- _o__register_onexit_function
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 051961f049109b4fa6a2881e442e621036cb279c
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913827"
---
# <a name="_execute_onexit_table-_initialize_onexit_table-_register_onexit_function"></a>_execute_onexit_table、_initialize_onexit_table、_register_onexit_function

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

*函數*<br/>
[in] 要新增至 onexit 函式表中的函式指標。

## <a name="return-value"></a>傳回值

如果成功，會傳回 0。 否則，傳回負值。

## <a name="remarks"></a>備註

這些函式是用來支援 C 執行階段的基礎結構實作詳細資料，不應該直接從程式碼呼叫。 C 執行時間會使用*onexit 函數表*，來代表呼叫`atexit`、 `at_quick_exit`和`_onexit`所註冊的函式序列。 Onexit 函式表資料結構是不透明的 C 執行階段實作詳細資料，其資料成員的順序和意義可能會變更。 它們不該由外部程式碼檢查。

`_initialize_onexit_table` 函式會將 onexit 函式表初始化為其初始值。  必須先呼叫此函式，再將 onexit 函式表傳遞至 `_register_onexit_function` 或 `_execute_onexit_table`。

`_register_onexit_function` 函式會將某個函式附加至 onexit 函式表的結尾。

`_execute_onexit_table` 函式會執行 onexit 函式表中所有的函式、清除資料表，然後傳回。 呼叫 `_execute_onexit_table` 之後，資料表即為非有效狀態，必須先呼叫 `_initialize_onexit_table` 重新初始化才能再次使用資料表。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`_initialize_onexit_table function`, `_register_onexit_function`, `_execute_onexit_table`|\<process.h>|

`_initialize_onexit_table`、 `_register_onexit_function`和`_execute_onexit_table`函式是 Microsoft 特有的。 如需相容性資訊，請參閱[相容性](../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[atexit](../c-runtime-library/reference/atexit.md)<br/>
[exit、_Exit、_exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_onexit、_onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)
