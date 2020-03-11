---
title: '&lt;random&gt; 函式'
ms.date: 09/04/2019
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: 3d94f607fc6b7bdf22d7f573f590b451dbaa718d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78873931"
---
# <a name="ltrandomgt-functions"></a>&lt;random&gt; 函式

## <a name="generate_canonical"></a>generate_canonical

從隨機序列傳回浮點值。

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>參數

*RealType*\
浮點整數類型。 如需可能的類型，請參閱 [\<random>](../standard-library/random.md)。

*Bits*\
要使用的隨機位數。

產生*器\*
亂數產生器類別。

*Gen*\
型別產生器的*亂數產生器實例*的參考。

### <a name="remarks"></a>備註

範本函式會重複呼叫*Gen* `operator()`，並將傳回的值封裝為*RealType*類型的浮點值 `x`，直到它在 `x`中收集到指定的尾數位數目為止。 指定的數位是較小的*位*（不能為零），而*RealType*中的尾數位則是完整數目。 第一次呼叫會提供最低位位元數。 此函式會傳回 `x`。
