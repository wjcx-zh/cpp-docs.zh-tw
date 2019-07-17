---
title: '&lt;limits&gt;'
ms.date: 11/04/2016
f1_keywords:
- limits/std::<limits>
- <limits>
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
ms.openlocfilehash: e23c47b3eaecec92e462af7b2cc47627c5bad86a
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245322"
---
# <a name="ltlimitsgt"></a>&lt;limits&gt;

定義範本類別 `numeric_limits` 和兩個關於浮點表示法和捨入的列舉。

## <a name="requirements"></a>需求

**標頭：** \<limits>

**命名空間：** std

## <a name="remarks"></a>備註

明確特製化`numeric_limits`類別描述的基本類型，包括字元、 整數和浮點類型的許多屬性和**bool**所定義，而不是由固定的實作規則的C++語言。 \<limits> 中所描述的屬性包括精確度、最小和最大表示法、捨入和訊號類型錯誤。

## <a name="members"></a>成員

### <a name="enumerations"></a>列舉

|||
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|此列舉會說明實作可選擇用來代表反正規化浮點值的各種方法 (反正規化浮點值是指太小而無法表示為正規化值的值)：|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|此列舉會說明實作可選擇用來將浮點值捨入為整數值的各種方法。|

### <a name="classes"></a>類別

|||
|-|-|
|[numeric_limits 類別](../standard-library/numeric-limits-class.md)|此範本類別可說明內建數值類型的算術屬性。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
