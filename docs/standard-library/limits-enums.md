---
title: '&lt;limits&gt; 列舉'
ms.date: 11/04/2016
f1_keywords:
- limits/std::float_denorm_style
- limits/std::float_round_style
ms.assetid: c86680a2-ba97-4ed9-8c20-a448857d7dc5
ms.openlocfilehash: 567e0538f59c40d57f85d652a8919be6e034cf0b
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420068"
---
# <a name="ltlimitsgt-enums"></a>&lt;limits&gt; 列舉

## <a name="float_denorm_style"></a>float_denorm_style

此列舉會說明實作可選擇用來代表反正規化浮點值的各種方法 (反正規化浮點值是指太小而無法表示為正規化值的值)：

```cpp
enum float_denorm_style {
    denorm_indeterminate = -1,
    denorm_absent = 0,
    denorm_present = 1    };
```

### <a name="return-value"></a>傳回值

此列舉會傳回：

- `denorm_indeterminate` 是否無法在轉譯時判斷反正規化形式的存在與否。

- 如果不存在反正規化的表單，`denorm_absent`。

- `denorm_present` 是否出現反正規化的表單。

### <a name="example"></a>範例

如需可存取此列舉之值的範例，請參閱 [numeric_limits::has_denorm](../standard-library/numeric-limits-class.md#has_denorm)。

## <a name="float_round_style"></a>float_round_style

此列舉會說明實作可選擇用來將浮點值捨入為整數值的各種方法。

```cpp
enum float_round_style {
    round_indeterminate = -1,
    round_toward_zero = 0,
    round_to_nearest = 1,
    round_toward_infinity = 2,
    round_toward_neg_infinity = 3    };
```

### <a name="return-value"></a>傳回值

此列舉會傳回：

- 如果無法判斷進位方法，`round_indeterminate`。

- 如果向零進行舍入 `round_toward_zero`。

- 如果四捨五入至最接近的整數，則 `round_to_nearest`。

- 如果從零四捨五入，`round_toward_infinity`。

- 如果舍入為較大的負整數，`round_toward_neg_infinity`。

### <a name="example"></a>範例

如需可存取此列舉之值的範例，請參閱 [numeric_limits::round_style](../standard-library/numeric-limits-class.md#round_style)。
