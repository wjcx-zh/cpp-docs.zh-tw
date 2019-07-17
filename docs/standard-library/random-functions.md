---
title: '&lt;random&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: 87b640d4f3aa3fbfa23ad5603d84102301e71ea4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240392"
---
# <a name="ltrandomgt-functions"></a>&lt;random&gt; 函式

## <a name="generate_canonical"></a> generate_canonical

從隨機序列傳回浮點值。

> [!NOTE]
> ISO C++ 標準規定此函式應傳回範圍 [`0`, `1`) 中的值。 Visual Studio 尚未與此條件約束相容。 作為在此範圍中產生值的解決辦法，請使用 [uniform_real_distribution](../standard-library/uniform-real-distribution-class.md)。

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>參數

*RealType*\
浮點整數類型。 如需可能的類型，請參閱 [\<random>](../standard-library/random.md)。

*位元*\
亂數產生器。

*一般*\
亂數產生器。

### <a name="remarks"></a>備註

範本函式會呼叫`operator()`的*Gen*重複和組件傳回的值，轉換浮點數的值`x`型別的*RealType*直到它已收集了指定的數目尾數中的位元`x`。 指定的數字是較小的一個*位元*（其必須為非零） 和完整的尾數中的位元數目*RealType*。 第一次呼叫會提供最低位位元數。 函式會傳回 `x`。
