---
title: '&lt;random&gt; 函式'
ms.date: 09/04/2019
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: 3d94f607fc6b7bdf22d7f573f590b451dbaa718d
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273831"
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

*一些*\
要使用的隨機位數。

*發電機*\
亂數產生器類別。

*代*\
型別產生器的亂數產生器實例的參考。

### <a name="remarks"></a>備註

範本函式會`operator()`重複呼叫*Gen* , 並將傳回的值封裝為*RealType*類型的`x`浮點值, 直到它在中`x`收集到指定的尾數位數為止。 指定的數位是較小的*位*(不能為零), 而*RealType*中的尾數位則是完整數目。 第一次呼叫會提供最低位位元數。 函式會傳回 `x`。
