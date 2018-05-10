---
title: steady_clock 結構 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::steady_clock
dev_langs:
- C++
ms.assetid: 970d12ec-fc80-4391-a2f7-b57b2aec668d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1dbfac1eb8c67c5306bded6e6fd9ee8dacf54b0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="steadyclock-struct"></a>steady_clock 結構

代表 `steady` 時鐘。

## <a name="syntax"></a>語法

```cpp
struct steady_clock;
```

## <a name="remarks"></a>備註

在 Windows 中，steady_clock 會包裝 QueryPerformanceCounter 函式。

如果第一次呼叫 `now()` 傳回的值一律小於或等於後續呼叫 `now()` 所傳回的值，則時鐘具「單一性」。

如果時鐘具「單一性」且時鐘刻度之間的時間固定，則時鐘具「穩定性」。

High_resolution_clock 是 steady_clock 的 typdef。

## <a name="public-functions"></a>公用函式

|功能|描述|
|--------------|-----------------|
|now|傳回目前的時間做為 time_point 值。|

## <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|`system_clock::is_steady`|保有 `true` `steady_clock` 為 steady。|

## <a name="requirements"></a>需求

**標頭：** \<chrono >

**命名空間：** std::chrono

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
[system_clock 結構](../standard-library/system-clock-structure.md)<br/>
