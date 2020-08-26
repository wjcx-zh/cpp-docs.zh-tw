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
ms.openlocfilehash: a79cb91a6b0e6ca633540fd37f7a0e1ece53b712
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845780"
---
# <a name="steady_clock-struct"></a>steady_clock 結構

代表 *high_resolution* 時鐘。

## <a name="syntax"></a>語法

```cpp
class high_resolution_clock
```

## <a name="members"></a>成員

### <a name="typedefs"></a>Typedefs

|名稱|描述|
|----------|-----------------|
|`duration`|`nanoseconds`中定義的同義字 \<chrono> 。|
|`period`|`nano`中定義的同義字 \<ratio> 。|
|`rep`|的同義字 **`long long`** ，這是用來表示內含具現化中的時鐘刻度數目的型別 `duration` 。|
|`time_point`|`chrono::time_point<high_resolution_clock>` 的同義字。|

## <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|`now`|以值形式傳回目前的時間 `time_point` 。|

## <a name="constants"></a>常數

|名稱|描述|
|----------|-----------------|
|`is_steady`|保存 **`true`** 。 `high_resolution_clock` 為 steady**。|
