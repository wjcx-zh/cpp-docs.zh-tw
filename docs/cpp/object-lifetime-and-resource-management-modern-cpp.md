---
title: 物件存留期和資源管理（RAII）
description: 請遵循最新的 RAII 原則C++ ，以避免資源流失。
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 8aa0e1a1-e04d-46b1-acca-1d548490700f
ms.openlocfilehash: 01867ec0a71ba54bb6534da1b408cb0610d652a7
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303372"
---
# <a name="object-lifetime-and-resource-management-raii"></a>物件存留期和資源管理（RAII）

不同于 managed 語言C++ ，並不會自動進行*垃圾收集*。 這是內部進程，會在程式執行時釋放堆積記憶體和其他資源。 C++程式會負責將所有取得的資源傳回作業系統。 無法釋放未使用的資源稱為「流失 *」。* 在進程結束之前，其他程式無法使用流失的資源。 記憶體流失特別是 C 樣式程式設計中錯誤的常見原因。

新式C++可避免在堆疊上宣告物件，盡可能使用堆積記憶體。 當資源對堆疊而言太大時，它應該會由物件*所擁有*。 當物件初始化時，它會取得它所擁有的資源。 物件接著會負責釋放其析構函式中的資源。 擁有物件本身會在堆疊上宣告。 *物件本身資源*的原則也稱為「資源取得初始化」或 RAII。

當資源擁有堆疊物件超出範圍時，就會自動叫用其析構函式。 如此一來，中C++的垃圾收集與物件存留期緊密相關，而且具決定性。 資源一律會在程式中的已知點釋放，您可以加以控制。 只有像 C++ 中的那些具決定性的解構函式能均衡處理記憶體和非記憶體資源。

下列範例顯示簡單的物件 `w`。 它會在函式範圍的堆疊上宣告，並在函式區塊的結尾終結。 物件 `w` 不會擁有任何*資源*（例如堆積配置的記憶體）。 其唯一的成員 `g` 本身會在堆疊上宣告，而且只會隨著 `w`而超出範圍。 `widget` 的析構函式中不需要任何特殊的程式碼。

```cpp
class widget {
private:
    gadget g;   // lifetime automatically tied to enclosing object
public:
    void draw();
};

void functionUsingWidget () {
    widget w;   // lifetime automatically tied to enclosing scope
                // constructs w, including the w.g gadget member
    // ...
    w.draw();
    // ...
} // automatic destruction and deallocation for w and w.g
  // automatic exception safety,
  // as if "finally { w.dispose(); w.g.dispose(); }"
```

在下列範例中，`w` 擁有記憶體資源，因此在其析構函式中必須有程式碼來刪除記憶體。
 
```cpp
class widget
{
private:
    int* data;
public:
    widget(const int size) { data = new int[size]; } // acquire
    ~widget() { delete[] data; } // release
    void do_something() {}
};

void functionUsingWidget() {
    widget w(1000000);   // lifetime automatically tied to enclosing scope
                        // constructs w, including the w.data member
    w.do_something();

} // automatic destruction and deallocation for w and w.data

```

自 c + + 11 開始，有更好的方法可以撰寫先前的範例：使用標準程式庫中的智慧型指標。 智慧型指標會處理所擁有之記憶體的配置和刪除。 使用智慧型指標，就不需要 `widget` 類別中的明確析構函式。

```cpp
#include <memory>
class widget
{
private:
    std::unique_ptr<int> data;
public:
    widget(const int size) { data = std::make_unique<int>(size); }
    void do_something() {}
};

void functionUsingWidget() {
    widget w(1000000);   // lifetime automatically tied to enclosing scope
                // constructs w, including the w.data gadget member
    // ...
    w.do_something();
    // ...
} // automatic destruction and deallocation for w and w.data

```

藉由使用智慧型指標進行記憶體配置，您可以消除記憶體流失的可能性。 此模型適用于其他資源，例如檔案控制代碼或通訊端。 您可以在類別中以類似的方式管理您自己的資源。 如需詳細資訊，請參閱[智慧型指標](smart-pointers-modern-cpp.md)。

的設計C++可確保物件在超出範圍時終結。 也就是說，它們會被終結，因為區塊會以相反的結構順序結束。 在物件終結時，它的基底和成員會以特殊的順序終結。 在全域範圍的任何區塊外宣告的物件，可能會導致問題。 如果全域物件的函式擲回例外狀況，可能會很難以進行 debug。

## <a name="see-also"></a>另請參閱

[歡迎回到C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)
