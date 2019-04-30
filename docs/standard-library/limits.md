---
title: '&lt;limits&gt;'
ms.date: 11/04/2016
f1_keywords:
- limits/std::<limits>
- <limits>
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
ms.openlocfilehash: c029095d5298048874a7eb6f1a41209d6a6f4779
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413238"
---
# <a name="ltlimitsgt"></a>&lt;limits&gt;

定義範本類別 `numeric_limits` 和兩個關於浮點表示法和捨入的列舉。

## <a name="syntax"></a>語法

```cpp
#include <limits>
```

## <a name="remarks"></a>備註

明確特製化`numeric_limits`類別描述的基本類型，包括字元、 整數和浮點類型的許多屬性和**bool**所定義，而不是由固定的實作規則的C++語言。 \<limits> 中所描述的屬性包括精確度、最小和最大表示法、捨入和訊號類型錯誤。

### <a name="enumerations"></a>列舉

|||
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|此列舉會說明實作可選擇用來代表反正規化浮點值的各種方法 (反正規化浮點值是指太小而無法表示為正規化值的值)：|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|此列舉會說明實作可選擇用來將浮點值捨入為整數值的各種方法。|

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[numeric_limits 類別](../standard-library/numeric-limits-class.md)|此範本類別可說明內建數值類型的算術屬性。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
