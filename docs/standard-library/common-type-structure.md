---
title: common_type 結構
ms.date: 11/04/2016
f1_keywords:
- chrono/std::common_type
ms.assetid: 2b42722c-c3dc-4d62-8613-0271e52b6f00
ms.openlocfilehash: cef9b1fb6bc2723de1202b63ddc711ddd39f0d97
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689808"
---
# <a name="common_type-structure"></a>common_type 結構

描述針對[duration](../standard-library/duration-class.md)和[time_point](../standard-library/time-point-class.md)的具現化之類別樣板[common_type](../standard-library/common-type-class.md)的特殊化。

## <a name="syntax"></a>語法

```cpp
template <class Rep1, class Period1,
    class Rep2, class Period2>
struct common_type
<chrono::duration<Rep1, Period1>,
chrono::duration<Rep2, Period2>>;

template <class Clock,
    class Duration1, class Duration2>
struct common_type
<chrono::time_point<Clock, Duration1>,
chrono::time_point<Clock, Duration2>>;
```

## <a name="requirements"></a>需求

**標頭：** \<chrono >

**命名空間:** std

## <a name="see-also"></a>請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
