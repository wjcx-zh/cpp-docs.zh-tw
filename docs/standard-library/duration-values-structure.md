---
title: duration_values 結構
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::duration_values
- chrono/std::chrono::duration_values::max
- chrono/std::chrono::duration_values::min
- chrono/std::chrono::duration_values::zero
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
ms.openlocfilehash: e2c03b4540ea5f89843562d1310b71635b3bc259
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368737"
---
# <a name="duration_values-structure"></a>duration_values 結構

提供 [duration](../standard-library/duration-class.md) 範本參數 `Rep` 的特定值。

## <a name="syntax"></a>語法

```cpp
template <class Rep>
struct duration_values;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[麥克斯](#max)|靜態。 指定 `Rep` 類型的值上限。|
|[分鐘](#min)|靜態。 指定 `Rep` 類型的值下限。|
|[零](#zero)|靜態。 傳回 `Rep(0)`。|

## <a name="requirements"></a>需求

**標題:**\<計時>

**命名空間：** std::chrono

## <a name="duration_valuesmax"></a><a name="max"></a>duration_values:最大

靜態方法會傳回型別 `Ref` 的上限值。

```cpp
static constexpr Rep max();
```

### <a name="return-value"></a>傳回值

實際上，系統會傳回 `numeric_limits<Rep>::max()`。

### <a name="remarks"></a>備註

當 `Rep` 是使用者定義的類型時，傳回的值必須大於 [duration_values::zero](#zero)。

## <a name="duration_valuesmin"></a><a name="min"></a>duration_values:分鐘

靜態方法會傳回型別 `Ref` 的下限值。

```cpp
static constexpr Rep min();
```

### <a name="return-value"></a>傳回值

實際上，系統會傳回 `numeric_limits<Rep>::lowest()`。

### <a name="remarks"></a>備註

當 `Rep` 是使用者定義的類型時，傳回的值必須小於或等於 [duration_values::zero](#zero)。

## <a name="duration_valueszero"></a><a name="zero"></a>duration_values::零

傳回 `Rep(0)`。

```cpp
static constexpr Rep zero();
```

### <a name="remarks"></a>備註

當 `Rep` 是使用者定義型別時，傳回值必須代表加法類無限大。

## <a name="see-also"></a>另請參閱

[標題檔案參考](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
