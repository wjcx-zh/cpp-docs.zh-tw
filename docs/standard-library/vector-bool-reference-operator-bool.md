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
ms.openlocfilehash: bb757fee9d6ec824a99557c409b1c4f02f48db5d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215383"
---
# <a name="vectorltboolgtreferenceoperator-bool"></a>vector&lt;bool&gt;::reference::operator bool

提供從到的隱含 `vector<bool>::reference` 轉換 **`bool`** 。

## <a name="syntax"></a>語法

```cpp
operator bool() const;
```

## <a name="return-value"></a>傳回值

[Vector \<bool> ](../standard-library/vector-bool-class.md)物件之元素的布林值。

## <a name="remarks"></a>備註

這個運算子無法修改 `vector<bool>` 物件。

## <a name="requirements"></a>需求

**標頭：**\<vector>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[vector \<bool> ：： Reference 類別](../standard-library/vector-bool-reference-class.md)\
[C + + 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
