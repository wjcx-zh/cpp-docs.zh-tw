---
title: steady_clock 結構 | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2018
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
ms.openlocfilehash: 5445379597c4fefcd657303a05c33b6509d54d2e
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569894"
---
# <a name="steadyclock-struct"></a>steady_clock 結構

代表*穩定*時鐘。

## <a name="syntax"></a>語法

```cpp
struct steady_clock;
```

## <a name="remarks"></a>備註

在 Windows 中，`steady_clock`包裝`QueryPerformanceCounter`函式。

如果第一次呼叫 `now` 傳回的值一律小於或等於後續呼叫 `now` 所傳回的值，則時鐘具「單一性」。 如果時鐘具「單一性」且時鐘刻度之間的時間固定，則時鐘具「穩定性」。

`high_resolution_clock` 是的 typedef `steady_clock`。

### <a name="public-typedefs"></a>公用 typedefs

|名稱|描述|
|----------|-----------------|
|`steady_clock::duration`|同義字`nanoseconds`，定義在\<chrono >。|
|`steady_clock::period`|同義字`nano`，定義在\<比率 >。|
|`steady_clock::rep`|同義字**長****長**，用來代表包含具現化的時脈週期數目的型別`duration`。|
|`steady_clock::time_point`|`chrono::time_point<steady_clock>` 的同義字。|

## <a name="public-functions"></a>公用函式

|功能|描述|
|--------------|-----------------|
|`now`|傳回目前的時間為`time_point`值。|

## <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|`steady_clock::is_steady`|保有 `true` `steady_clock` 為 steady。|

## <a name="requirements"></a>需求

**標頭：** \<chrono >

**命名空間：** std::chrono

## <a name="see-also"></a>另請參閱

- [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
- [\<chrono>](../standard-library/chrono.md)
- [system_clock 結構](../standard-library/system-clock-structure.md)
