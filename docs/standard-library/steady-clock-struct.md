---
title: steady_clock 結構
ms.date: 05/22/2018
f1_keywords:
- chrono/std::chrono::steady_clock
ms.assetid: 970d12ec-fc80-4391-a2f7-b57b2aec668d
ms.openlocfilehash: d21d5c2ed7ed667333007f3bd12d13f47b868380
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217398"
---
# <a name="steady_clock-struct"></a>steady_clock 結構

表示*穩定*的時鐘。

## <a name="syntax"></a>語法

```cpp
struct steady_clock;
```

## <a name="remarks"></a>備註

在 Windows 上，包裝函式 `steady_clock` `QueryPerformanceCounter` 。

如果第一次呼叫 `now` 傳回的值一律小於或等於後續呼叫 `now` 所傳回的值，則時鐘具「單一性」**。 如果時鐘具「單一性」** 且時鐘刻度之間的時間固定，則時鐘具「穩定性」**。

`high_resolution_clock`是的 typedef `steady_clock` 。

### <a name="public-typedefs"></a>公用 typedef

|名稱|說明|
|----------|-----------------|
|`steady_clock::duration`|的同義字 `nanoseconds` ，定義于中 \<chrono> 。|
|`steady_clock::period`|的同義字 `nano` ，定義于中 \<ratio> 。|
|`steady_clock::rep`|的同義字 **`long long`** ，這是用來代表所包含之具現化中之時鐘刻度數的類型 `duration` 。|
|`steady_clock::time_point`|`chrono::time_point<steady_clock>` 的同義字。|

## <a name="public-functions"></a>公用函式

|函式|說明|
|--------------|-----------------|
|`now`|傳回目前的時間做為 `time_point` 值。|

## <a name="public-constants"></a>公用常數

|名稱|說明|
|----------|-----------------|
|`steady_clock::is_steady`|保存 **`true`** 。 `steady_clock` 為 steady**。|

## <a name="requirements"></a>需求

**標頭：**\<chrono>

**命名空間：** std::chrono

## <a name="see-also"></a>另請參閱

- [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
- [\<chrono>](../standard-library/chrono.md)
- [system_clock 結構](../standard-library/system-clock-structure.md)
