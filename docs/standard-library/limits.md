---
title: '&lt;limits&gt;'
ms.date: 11/04/2016
f1_keywords:
- limits/std::<limits>
- <limits>
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
ms.openlocfilehash: 2d0f4f96d25c91ac20fe5a1883fc61fc47d15d5e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217684"
---
# <a name="ltlimitsgt"></a>&lt;limits&gt;

定義類別樣板 `numeric_limits` 和兩個關於浮點表示和舍入的列舉。

## <a name="requirements"></a>需求

**標頭：**\<limits>

**命名空間：** std

## <a name="remarks"></a>備註

類別的明確特製化 `numeric_limits` 描述基本類型的許多屬性，包括字元、整數和浮點類型，以及 **`bool`** 已定義實作為，而不是由 c + + 語言的規則修正。 中所述的屬性 \<limits> 包括精確度、最小和最大大小的標記法、進位和信號類型錯誤。

## <a name="members"></a>成員

### <a name="enumerations"></a>列舉

|||
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|此列舉會說明實作可選擇用來代表反正規化浮點值的各種方法 (反正規化浮點值是指太小而無法表示為正規化值的值)：|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|此列舉會說明實作可選擇用來將浮點值捨入為整數值的各種方法。|

### <a name="classes"></a>類別

|||
|-|-|
|[numeric_limits 類別](../standard-library/numeric-limits-class.md)|類別範本會描述內建數數值型別的算術屬性。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
