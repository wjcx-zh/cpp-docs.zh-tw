---
title: linear_congruential_engine 類別
ms.date: 11/04/2016
f1_keywords:
- random/std::linear_congruential_engine
helpviewer_keywords:
- linear_congruential_engine class
ms.assetid: 30e00ca6-1933-4701-9561-54f3e810a5a1
ms.openlocfilehash: 8701570787275e853543e723f6461b8ad460f96f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845441"
---
# <a name="linear_congruential_engine-class"></a>linear_congruential_engine 類別

依線性同餘演算法產生隨機序列。

## <a name="syntax"></a>語法

```cpp
class linear_congruential_engine{
   public:  // types
   typedef UIntType result_type;
   // engine characteristics
   static constexpr result_type multiplier = a;
   static constexpr result_type increment = c;
   static constexpr result_type modulus = m;
   static constexpr result_type min() { return c == 0u  1u: 0u; }
   static constexpr result_type max() { return m - 1u; }
   static constexpr result_type default_seed = 1u;
   // constructors and seeding functions
   explicit linear_congruential_engine(result_type s = default_seed);
   template <class Sseq>
   explicit linear_congruential_engine(Sseq& q);
   void seed(result_type s = default_seed);
   template <class Sseq>
   void seed(Sseq& q);
   // generating functions
   result_type operator()();
   void discard(unsigned long long z);
   };
```

### <a name="parameters"></a>參數

*UIntType*\
不帶正負號的整數結果類型。 如需可能的類型，請參閱 [\<random>](../standard-library/random.md) 。

*的*\
**乘數**。 **前置條件**：請參閱＜備註＞一節。

*C*\
**遞增**。 **前置條件**：請參閱＜備註＞一節。

*M*\
**模數**。 **前置條件**：請參閱備註。

## <a name="members"></a>成員

`linear_congruential_engine::linear_congruential_engine`
`linear_congruential_engine::discard`\
`linear_congruential_engine::max`\
`linear_congruential_engine::min`\
`linear_congruential_engine::operator()`\
`linear_congruential_engine::seed`

`default_seed` 是一個成員常數，定義為 `1u`，用做 `linear_congruential_engine::seed` 的預設參數值以及單一值建構函式。

如需引擎成員的詳細資訊，請參閱 [\<random>](../standard-library/random.md) 。

## <a name="remarks"></a>備註

`linear_congruential_engine`類別樣板是最簡單的產生器引擎，但不是最快或最高的品質。 和此引擎相較之下較為改進的是 [substract_with_carry_engine](../standard-library/subtract-with-carry-engine-class.md)。 但這些引擎都不像 [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md) 一樣快，且具有高品質的結果。

此引擎會使用週期性關聯 ( *期間*) 來產生使用者指定之不帶正負號的整數類型的值 `x(i) = (A * x(i-1) + C) mod M` 。

如果 *M* 為零，則用於此模數運算的值為 `numeric_limits<result_type>::max() + 1` 。 引擎的狀態會是上次傳回的值；若沒有對 `operator()` 執行任何呼叫，則引擎的狀態是初始值。

如果 *M* 不是零，則範本引數 *A* 和 *C* 的值必須小於 *M*。

雖然您可以直接從此引擎建構產生器，但您也可以使用下列其中一個預先定義的 typedef。

`minstd_rand0`：1988 最低標準引擎 (Lewis、Goodman 及 Miller，1969 年)。

```cpp
typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;
```

`minstd_rand`：更新的最低標準引擎 `minstd_rand0` (Park、Miller 及 Stockmeyer，1993 年)。

```cpp
typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;
```

如需有關線性同餘引擎演算法的詳細資訊，請參閱 Wikipedia 文章[線性同餘方法](https://go.microsoft.com/fwlink/p/?linkid=402446)。

## <a name="requirements"></a>規格需求

**標頭：**\<random>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[\<random>](../standard-library/random.md)
