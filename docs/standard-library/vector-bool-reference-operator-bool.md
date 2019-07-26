---
title: vector&lt;bool&gt;::reference::operator bool
ms.date: 11/04/2016
f1_keywords:
- operatorbool
- vector<bool>::reference::operatorbool
- bool
- std::vector<bool>::reference::operatorbool
helpviewer_keywords:
- BOOL operator
- reference::operator bool
ms.assetid: b0e57869-18cc-4296-9061-da502f30120d
ms.openlocfilehash: ca2d21a7706248cd84ca3591eb717e4081972f9c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452127"
---
# <a name="vectorltboolgtreferenceoperator-bool"></a>vector&lt;bool&gt;::reference::operator bool

提供從`vector<bool>::reference`到**bool**的隱含轉換。

## <a name="syntax"></a>語法

```cpp
operator bool() const;
```

## <a name="return-value"></a>傳回值

[vector\<bool>](../standard-library/vector-bool-class.md) 物件項目的布林值。

## <a name="remarks"></a>備註

這個運算子無法修改 `vector<bool>` 物件。

## <a name="requirements"></a>需求

**標頭：** \<vector>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[vector\<bool>::reference 類別](../standard-library/vector-bool-reference-class.md)\
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
