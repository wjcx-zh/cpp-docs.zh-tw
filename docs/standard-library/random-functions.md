---
title: '&lt;random&gt; 函式 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: e01c1d71cbc0b3990e40a38484cc9c7a2cc3ebcc
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44102794"
---
# <a name="ltrandomgt-functions"></a>&lt;random&gt; 函式

## <a name="generate_canonical"></a>  generate_canonical

從隨機序列傳回浮點值。

> [!NOTE]
> ISO C++ 標準規定此函式應傳回範圍 [`0`, `1`) 中的值。 Visual Studio 尚未與此條件約束相容。 作為在此範圍中產生值的解決辦法，請使用 [uniform_real_distribution](../standard-library/uniform-real-distribution-class.md)。

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>參數

*RealType*<br/>
浮點整數類型。 如需可能的類型，請參閱 [\<random>](../standard-library/random.md)。

*位元*<br/>
亂數產生器。

*一般*<br/>
亂數產生器。

### <a name="remarks"></a>備註

範本函式會呼叫`operator()`的*Gen*重複和組件傳回的值，轉換浮點數的值`x`型別的*RealType*直到它已收集了指定的數目尾數中的位元`x`。 指定的數字是較小的一個*位元*（其必須為非零） 和完整的尾數中的位元數目*RealType*。 第一次呼叫會提供最低位位元數。 函式會傳回 `x`。

## <a name="see-also"></a>另請參閱

[\<random>](../standard-library/random.md)<br/>
