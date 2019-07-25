---
title: '&lt;limits&gt;'
ms.date: 11/04/2016
f1_keywords:
- limits/std::<limits>
- <limits>
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
ms.openlocfilehash: de8f815cd59b84a1e63c231e18e4882d0b5d6f09
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447577"
---
# <a name="ltlimitsgt"></a>&lt;limits&gt;

定義範本類別 `numeric_limits` 和兩個關於浮點表示法和捨入的列舉。

## <a name="requirements"></a>需求

**標頭：** \<limits>

**命名空間：** std

## <a name="remarks"></a>備註

類別的`numeric_limits`明確特製化描述許多基本類型的屬性, 包括字元、整數和浮點類型, 以及已定義實值的**bool** , 而不是由C++語言。 \<limits> 中所描述的屬性包括精確度、最小和最大表示法、捨入和訊號類型錯誤。

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

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
