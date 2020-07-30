---
title: operator &lt; 運算子（Microsoft：： WRL）
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::operator<
ms.assetid: bfae0e1c-1648-482b-99c2-3217d62aba46
ms.openlocfilehash: b438f823814e21e2da43f698471d782c88626628
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226876"
---
# <a name="operatorlt-operator-microsoftwrl"></a>operator &lt; 運算子（Microsoft：： WRL）

判斷一個物件的位址是否小於另一個。

## <a name="syntax"></a>語法

```cpp
template<class T, class U>
bool operator<(const ComPtr<T>& a, const ComPtr<U>& b) throw();
template<class T, class U>
bool operator<(const Details::ComPtrRef<ComPtr<T>>& a, const Details::ComPtrRef<ComPtr<U>>& b) throw();
```

### <a name="parameters"></a>參數

*為*<br/>
左物件。

*位元組*<br/>
右物件。

## <a name="return-value"></a>傳回值

**`true`** 如果的位址小於*b*的位址，則*為，* 否則為 **`false`** 。

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft：： WRL 命名空間](microsoft-wrl-namespace.md)
