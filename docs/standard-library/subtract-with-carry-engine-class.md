---
title: subtract_with_carry_engine 類別
ms.date: 11/04/2016
f1_keywords:
- random/std::subtract_with_carry_engine
- random/std::subtract_with_carry_engine::default_seed
- random/std::subtract_with_carry_engine::discard
- random/std::subtract_with_carry_engine::min
- random/std::subtract_with_carry_engine::max
- random/std::subtract_with_carry_engine::seed
helpviewer_keywords:
- std::subtract_with_carry_engine [C++]
- std::subtract_with_carry_engine [C++], default_seed
- std::subtract_with_carry_engine [C++], discard
- std::subtract_with_carry_engine [C++], min
- std::subtract_with_carry_engine [C++], max
- std::subtract_with_carry_engine [C++], seed
ms.assetid: 94a055f2-a620-4a22-ac34-c156924bab31
ms.openlocfilehash: cf82c4ca3ce995fa9a53dbea21293dc8515ff491
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840904"
---
# <a name="subtract_with_carry_engine-class"></a>subtract_with_carry_engine 類別

使用帶進位減法 (延隔 Fibonacci) 演算法，以產生隨機序列。

## <a name="syntax"></a>語法

```cpp
template <class UIntType, size_t W, size_t S, size_t R>
class subtract_with_carry_engine;
```

### <a name="parameters"></a>參數

*UIntType*\
不帶正負號的整數結果類型。 如需可能的類型，請參閱 [\<random>](../standard-library/random.md) 。

*W*\
**字組大小**。 狀態序列的每個字組大小 (位元)。 **前置條件**： `0 < W ≤ numeric_limits<UIntType>::digits`

*！*\
**短延隔**。 整數值數目。 **前置條件**： `0 < S < R`

*R*\
**長延隔**。 決定所產生數列中的週期。

## <a name="members"></a>成員

`subtract_with_carry_engine::subtract_with_carry_engine`
`subtract_with_carry_engine::max`\
`subtract_with_carry_engine::min`\
`subtract_with_carry_engine::discard`\
`subtract_with_carry_engine::operator()`\
`subtract_with_carry_engine::seed`

`default_seed` 是一個成員常數，定義為 `19780503u`，用做 `subtract_with_carry_engine::seed` 的預設參數值以及單一值建構函式。

如需引擎成員的詳細資訊，請參閱 [\<random>](../standard-library/random.md) 。

## <a name="remarks"></a>備註

`substract_with_carry_engine`類別樣板是[linear_congruential_engine](../standard-library/linear-congruential-engine-class.md)的改善。 但這些引擎都不像 [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md) 一樣快，且具有高品質的結果。

此引擎會使用週期性關聯 (*期間*) 來產生使用者指定之不帶正負號的整數類型的值 `x(i) = (x(i - R) - x(i - S) - cy(i - 1)) mod M` ，其中的值為 `cy(i)` `1` ，如果為，則為，而值 `x(i - S) - x(i - R) - cy(i - 1) < 0` `0` `M` 為 `2` <sup>W</sup>。引擎的狀態是帶有帶有指標和*R*值。 這些值包含最後一個傳回的 *r* 值 `operator()` （如果至少已呼叫 *r* 次），否則就是 `N` 傳回的值以及種子的最後一個 `R - N` 值。

範本引數 `UIntType` 必須夠大，才能保留最多 `M - 1` 個值。

雖然您可以直接從此引擎建構產生器，但您也可以使用下列其中一個預先定義的 typedef：

`ranlux24_base`：用來做為 `ranlux24` 的基底。
`typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`

`ranlux48_base`：用來做為 `ranlux48` 的基底。
`typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`

如需帶進位減法引擎演算法的詳細資訊，請參閱維基百科文章：[延隔 Fibonacci 產生器 (英文)](https://en.wikipedia.org/wiki/Lagged_Fibonacci_generator)。

## <a name="requirements"></a>規格需求

**標頭：**\<random>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[\<random>](../standard-library/random.md)
