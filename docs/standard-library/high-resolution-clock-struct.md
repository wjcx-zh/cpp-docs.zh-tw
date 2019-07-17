---
title: high_resolution_clock 結構 |Microsoft Docs
ms.custom: ''
ms.date: 05/22/2018
ms.technology: cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::high_resolution_clock
dev_langs:
- C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b00b20e7cea4fa24b37ad33d5536eb9844e6953
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269120"
---
# <a name="steadyclock-struct"></a>steady_clock 結構

代表*high_resolution*時鐘。

## <a name="syntax"></a>語法

```cpp
class high_resolution_clock
```

## <a name="members"></a>成員

### <a name="typedefs"></a>Typedefs

|名稱|說明|
|----------|-----------------|
|`duration`|同義字`nanoseconds`，其定義於\<chrono >。|
|`period`|同義字`nano`，其定義於\<比例 >。|
|`rep`|同義字**長** **長**，用來代表包含具現化的時鐘刻度數目的型別`duration`。|
|`time_point`|`chrono::time_point<high_resolution_clock>` 的同義字。|

## <a name="functions"></a>函式

|||
|-|-|
|`now`|傳回目前時間`time_point`值。|

## <a name="constants"></a>常數

|名稱|描述|
|----------|-----------------|
|`is_steady`|保存 **，則為 true**。 `high_resolution_clock` 為 steady  。|
