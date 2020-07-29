---
title: noexcept (C++)
ms.date: 11/19/2019
f1_keywords:
- noexcept_cpp
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
ms.openlocfilehash: 2618c7e9b35e4ba50ad1bda20a8694dd829ec2d8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223638"
---
# <a name="noexcept-c"></a>noexcept (C++)

**C + + 11：** 指定函式是否可能擲回例外狀況。

## <a name="syntax"></a>語法

> *noexcept-expression*： \
> &nbsp;&nbsp;&nbsp;&nbsp;**`noexcept`**\
> &nbsp;&nbsp;&nbsp;&nbsp;**noexcept （** *常數運算式* **）**

### <a name="parameters"></a>參數

*常數運算式*<br/>
類型的常數運算式 **`bool`** ，表示可能的例外狀況類型集合是否是空的。 無條件版本相當於 `noexcept(true)` 。

## <a name="remarks"></a>備註

*Noexcept 運算式*是一種例外狀況*規格*，也就是函式宣告的後置詞，代表一組可能會因任何結束函式之例外狀況的例外狀況處理常式而比對的類型。 一元條件運算子 `noexcept(` *constant_expression* `)` *constant_expression*產生的位置 **`true`** ，以及其無條件同義字，指定可以結束函式的 **`noexcept`** 可能例外狀況類型集合是空的。 也就是說，函式永遠不會擲回例外狀況，而且永遠不允許將例外狀況傳播到其範圍外。 Constant_expression 產生的運算子 `noexcept(` *constant_expression* `)` *constant_expression* **`false`** ，或缺少例外狀況規格（除了針對析構函數或解除配置函式以外），表示可以結束函數的一組可能的例外狀況是所有類型的集合。

**`noexcept`** 只有在直接或間接呼叫的所有函式都是或時，才將函式標示 **`noexcept`** 為 **`const`** 。 編譯器不一定會檢查每個程式碼路徑是否有可能會反升至函式的例外狀況 **`noexcept`** 。 如果例外狀況結束已標記之函式的外部範圍，則會立即叫用 **`noexcept`** [std：： terminate](../standard-library/exception-functions.md#terminate) ，而且不保證會叫用任何範圍內物件的析構函式。 使用 **`noexcept`** ，而不是動態例外狀況規範 `throw()` ，其現在已在標準中被取代。 我們建議您套用 **`noexcept`** 到任何不允許例外狀況傳播呼叫堆疊的函式。 宣告函式時 **`noexcept`** ，它可讓編譯器在數個不同的內容中產生更有效率的程式碼。 如需詳細資訊，請參閱[例外狀況規格](exception-specifications-throw-cpp.md)。

## <a name="example"></a>範例

複製其引數的樣板函式，可能會 **`noexcept`** 在要複製的物件為一般舊資料類型（POD）時宣告。 這類函式可以宣告如下：

```cpp
#include <type_traits>

template <typename T>
T copy_object(const T& obj) noexcept(std::is_pod<T>)
{
   // ...
}
```

## <a name="see-also"></a>另請參閱

[適用于例外狀況和錯誤處理的新式 c + + 最佳作法](errors-and-exception-handling-modern-cpp.md)<br/>
[例外狀況規格（throw，noexcept）](exception-specifications-throw-cpp.md)
