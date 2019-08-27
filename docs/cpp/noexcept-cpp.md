---
title: noexcept (C++)
ms.date: 01/12/2018
f1_keywords:
- noexcept_cpp
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
ms.openlocfilehash: cf53aca918e36d18ab7f8aa14b01caaf0e55627c
ms.sourcegitcommit: ace42fa67e704d56d03c03745b0b17d2a5afeba4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69975890"
---
# <a name="noexcept-c"></a>noexcept (C++)

**C + + 11:** 指定函式是否可能擲回例外狀況。

## <a name="syntax"></a>語法

> *noexcept-expression*: &nbsp;&nbsp;&nbsp;&nbsp;**noexcept** &nbsp;&nbsp;&nbsp;&nbsp;**noexcept(** *constant-expression* **)**

### <a name="parameters"></a>參數

*constant-expression*<br/>
**Bool**類型的常數運算式, 表示可能的例外狀況類型集合是否是空的。 無條件版本相當於`noexcept(true)`。

## <a name="remarks"></a>備註

*Noexcept 運算式*是一種例外狀況*規格*, 也就是函式宣告的後置詞, 代表一組可能會因任何結束函式之例外狀況的例外狀況處理常式而比對的類型。 一元條件運算子`noexcept(` *constant_expression* `)` , 其中*constant_expression*會產生**true**, 而其無條件同義字**noexcept**會指定一組可能的例外狀況類型,可以結束函數是空的。 也就是說, 函式永遠不會擲回例外狀況, 而且永遠不允許將例外狀況傳播到其範圍外。 運算子`noexcept(` *constant_expression*, 其中 constant_expression 會產生 false, 或缺少例外狀況規格 (針對析構函數或解除配置函式除外), 表示`)`可能會結束函式的可能例外狀況集合是所有類型的集合。

只有當直接或間接呼叫的所有函式都是**noexcept**或**const**時, 才將函數標記為**noexcept** 。 編譯器不一定會檢查每個程式碼路徑是否有可能會反升至**noexcept**函式的例外狀況。 如果例外狀況結束已標記`noexcept`之函式的外部範圍, 則會立即叫用[std:: terminate](../standard-library/exception-functions.md#terminate) , 而且不保證會叫用任何範圍內物件的析構函式。 請使用**noexcept** , 而不是動態`throw()`例外狀況規範, 其現在已在標準中被取代。 我們建議您`noexcept`套用到任何不允許例外狀況傳播呼叫堆疊的函式。 當函式宣告為**noexcept**時, 它可讓編譯器在數個不同的內容中產生更有效率的程式碼。 如需詳細資訊, 請參閱[例外狀況規格](exception-specifications-throw-cpp.md)。

## <a name="example"></a>範例

複製其引數的樣板函式, 可能會在所複製的物件為一般舊資料類型 (POD) 的條件上宣告為**noexcept** 。 這類函式可以宣告如下：

```cpp
#include <type_traits>

template <typename T>
T copy_object(const T& obj) noexcept(std::is_pod<T>)
{
   // ...
}
```

## <a name="see-also"></a>另請參閱

[C++ 例外狀況處理](cpp-exception-handling.md)<br/>
[例外狀況規格 (throw, noexcept)](exception-specifications-throw-cpp.md)