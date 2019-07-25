---
title: 容器類別::swap
ms.date: 11/04/2016
helpviewer_keywords:
- swap method
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
ms.openlocfilehash: ccf4ae6ebc3ca13a42ca950310a60e30dbb27034
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450763"
---
# <a name="container-classswap"></a>容器類別::swap

> [!NOTE]
> 本主題位於 Microsoft C++檔中, 做為C++標準程式庫中所使用之容器的無作用範例。 如需詳細資訊，請參閱 [C++ 標準程式庫容器](../standard-library/stl-containers.md)。

會交換 **\*this** 和其引數之間受控制的序列。

## <a name="syntax"></a>語法

```cpp
void swap(Container& right);
```

## <a name="remarks"></a>備註

若為 **\*this.get\_allocator ==** _right_ **.get_allocator**，則會在固定的時間進行交換。 否則，它會執行多個元素指派，和與兩個受控制序列中元素數目成正比的建構函式呼叫。

## <a name="see-also"></a>另請參閱

[範例容器類別](../standard-library/sample-container-class.md)
