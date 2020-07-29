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
ms.openlocfilehash: 850d5e3a5434aa44e23a7f74aeb9c306ab6c0a8e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203204"
---
# <a name="steady_clock-struct"></a>steady_clock 結構

表示*high_resolution*的時鐘。

## <a name="syntax"></a>語法

```cpp
class high_resolution_clock
```

## <a name="members"></a>成員

### <a name="typedefs"></a>Typedefs

|名稱|說明|
|----------|-----------------|
|`duration`|的同義字 `nanoseconds` ，定義于中 \<chrono> 。|
|`period`|的同義字 `nano` ，定義于中 \<ratio> 。|
|`rep`|的同義字 **`long long`** ，這是用來代表所包含之具現化中之時鐘刻度數的類型 `duration` 。|
|`time_point`|`chrono::time_point<high_resolution_clock>` 的同義字。|

## <a name="functions"></a>函式

|||
|-|-|
|`now`|傳回目前的時間做為 `time_point` 值。|

## <a name="constants"></a>常數

|名稱|說明|
|----------|-----------------|
|`is_steady`|保存 **`true`** 。 `high_resolution_clock` 為 steady**。|
