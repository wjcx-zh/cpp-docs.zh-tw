---
title: 值的類型語意 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interior_ptr keyword [C++]
- virtual functions, value types
- inheritance, value types
- pinning pointers
- pin_ptr keyword [C++]
- __pin keyword
ms.assetid: 7f065589-ad25-4850-baf1-985142e35e52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 72dc6a613616d13e9ff92e8af0c39c63dfe63162
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413792"
---
# <a name="value-type-semantics"></a>實值類型語意

實值類型語意變更從 Managed Extensions for c + + 為 Visual c + +。

以下是用於 Managed Extensions for c + + 規格的標準的簡單實值類型：

```
__value struct V { int i; };
__gc struct R { V vr; };
```

在 Managed Extensions，我們可以有四個實值類型的語法變化 （位置 2 和 3 的表單是相同語意）：

```
V v = { 0 };       // Form (1)
V *pv = 0;         // Form (2) an implicit form of (3)
V __gc *pvgc = 0;  // Form (3)
__box V* pvbx = 0; // Form (4) must be local
```

## <a name="invoking-inherited-virtual-methods"></a>叫用繼承虛擬方法

`Form (1)` 是標準值物件，並於合理範圍內了解，除了當有人嘗試叫用繼承虛擬方法時，例如`ToString()`。 例如: 

```
v.ToString(); // error!
```

若要叫用這個方法，因為未在覆寫`V`，編譯器必須能夠存取基底類別的相關聯的虛擬資料表。 因為實值型別沒有關聯的指標，其虛擬資料表 (vptr) 的狀態中儲存體，這需要`v`會進行 boxed 處理。 在 Managed Extensions 的語言設計，隱含 boxing 不支援，但必須明確地指定程式設計人員，如

```
__box( v )->ToString(); // Managed Extensions: note the arrow
```

此設計背後的主要動機是為了： 基礎機制必須是程式設計人員可以看到，使她就能了解不會提供在她的實值型別執行個體的 '成本'。 已`V`包含的執行個體`ToString`，boxing 就不一定需要。

新的語法中，已移除的明確 boxing 物件，但不是本身，boxing 的基礎成本語彙複雜度：

```
v.ToString(); // new syntax
```

但代價是可能產生誤導類別設計工具，並不需要提供明確的執行個體的成本`ToString`方法內`V`。 偏好隱含 boxing 的原因是通常是只在一個類別設計工具，雖然有無限的數量的使用者，他們全都會都可以自由修改`V`消除可能很繁重的明確方塊。

用來判斷是否要提供的覆寫執行個體的準則`ToString`類別內的值應該是頻率和其用法的位置。 如果呼叫很少，有當然是其定義的好處不大。 同樣地，如果呼叫它時，在非高效能的應用程式區域中，將它加入會也不適當地加入至應用程式的一般效能。 或者，其中可保留的追蹤控制代碼為 boxed 實值，並透過該控制代碼的呼叫者不需要 boxing。

## <a name="there-is-no-longer-a-value-class-default-constructor"></a>不再是值類別預設建構函式

與實值型別之間受管理的擴充功能和新語法中的另一個差異是支援的移除的預設建構函式。 這是因為有些情況下，可以在其中 CLR 建立的實值型別執行個體而不叫用相關聯的預設建構函式的執行期間。 也就是嘗試在 Managed Extensions 支援實值型別內的預設建構函式可能實際上不保證。 指定保證該不存在，它被認為最好一併卸除的支援，而不是讓它不具決定性在其應用程式中。

這不是因為它一開始看起來的錯誤。 這是因為實值類型的每個物件會自動去除 （也就是每個型別會初始化為其預設值）。 如此一來，一定會未定義的本機執行個體的成員。 在這種情況下，喪失的功能定義 trivial 預設建構函式其實根本不是遺失-和事實上是由 CLR 執行時，更有效率。

Managed Extensions 的使用者定義的非 trivial 預設建構函式時的問題。 這對於沒有對應至新語法。 建構函式中的程式碼必須是移轉至具名的初始設定方法，就必須由使用者明確地叫用。

新語法中的實值類型物件的宣告則未變更。 這個缺點是，實值型別不是令人滿意的原生型別換行的原因如下：

- 沒有解構函式內實值型別支援。 也就是沒有任何方法可以自動執行一組物件的存留期結束時所觸發的動作。

- 原生類別可以包含只在 managed 類型，然後在原生堆積上配置的指標。

我們想要包裝實值型別而不是參考型別來避免雙重的堆積配置的小型原生類別： 原生堆積，以保存原生型別，而 CLR 堆積來保留 managed 包裝函式。 包裝內實值類型的原生類別可讓您避免在 managed 的堆積，但不提供任何方法來自動執行的原生堆積記憶體回收。 參考型別是內用來包裝非一般的原生類別只是行不通的 managed 型別。

## <a name="interior-pointers"></a>內部指標

`Form (2)` 和`Form (3)`上方可以應付一切這個世界中的下一個 （也就是任何 managed 或原生）。 因此，比方說，下列所有允許受管理的擴充功能中：

```
__value struct V { int i; };
__gc struct R { V vr; };

V v = { 0 };  // Form (1)
V *pv = 0;  // Form (2)
V __gc *pvgc = 0;  // Form (3)
__box V* pvbx = 0;  // Form (4)

R* r;

pv = &v;            // address a value type on the stack
pv = __nogc new V;  // address a value type on native heap
pv = pvgc;          // we are not sure what this addresses
pv = pvbx;          // address a boxed value type on managed heap
pv = &r->vr;        // an interior pointer to value type within a
                    //    reference type on the managed heap
```

因此，`V*`可以解決在本機的區塊內的位置 （並因此可以懸空），在全域範圍內的原生堆積 （例如，如果已刪除其定址之物件），在 CLR 堆積 （且因此將會追蹤是否應該重新定位在記憶體回收期間），並在 CLR 堆積 （內部指標，因為這個呼叫時，也可以追蹤） 上的參考物件的內部。

在受管理的擴充功能中，沒有任何方法來區隔的原生層面`V*`; 也就是，則會視為在其內含處理定址的物件或子物件，在 managed 堆積上的可能性。

在新語法中，實值型別指標納入兩種類型： `V*`，這是限制為非 CLR 堆積位置和內部指標， `interior_ptr<V>`，其中提供，但不需要 managed 堆積內的位址。

```
// may not address within managed heap
V *pv = 0;

// may or may not address within managed heap
interior_ptr<V> pvgc = nullptr;
```

`Form (2)` 並`Form (3)`Managed Extensions 的對應到`interior_ptr<V>`。 `Form (4)` 是的追蹤控制代碼。 它可解決整個已將其 box managed 堆積內的物件。 它會轉譯成新的語法中`V^`，

```
V^ pvbx = nullptr; // __box V* pvbx = 0;
```

所有對應至新的語法中的內部指標的 Managed Extensions 中的下列宣告。 (它們是實值型別內`System`命名空間。)

```
Int32 *pi;   // => interior_ptr<Int32> pi;
Boolean *pb; // => interior_ptr<Boolean> pb;
E *pe;       // => interior_ptr<E> pe; // Enumeration
```

內建類型不會考慮 managed 型別，雖然它們執行做為別名的型別內`System`命名空間。 因此下列對應成立之間受管理的擴充功能和新的語法：

```
int * pi;     // => int* pi;
int __gc * pi2; // => interior_ptr<int> pi2;
```

當轉譯`V*`在您現有的程式中，最保守的策略是一律將它以`interior_ptr<V>`。 這是如何處理在受管理的擴充功能。 在新語法中，程式設計人員可以選擇藉由指定限制非受控堆積地址的實值型別`V*`而不是內部指標。 如果轉譯程式，您可以執行所有其使用可轉移關閉，並確定沒有指派的位址是 managed 堆積內，然後使其為`V*`沒問題。

## <a name="pinning-pointers"></a>Pin 指標

記憶體回收行程可能會選擇性地移動位於 CLR 堆積堆積內的不同位置，通常在壓縮階段期間的物件。 此移動不追蹤控制代碼、 追蹤參考和內部指標以透明的方式更新這些實體的問題。 不過，如果使用者已傳遞物件位址以外的執行階段環境在 CLR 堆積上時，此移動將會是問題。 在此情況下，動態移動物件很可能會導致執行階段失敗。 豁免的物件，例如從正在移動，我們必須在本機將它們釘選到其範圍外部使用的位置。

在受管理的擴充功能*pin 指標*宣告限定名稱的指標宣告`__pin`關鍵字。 以下是範例稍做修改，從 Managed Extensions 規格：

```
__gc struct H { int j; };

int main()
{
   H * h = new H;
   int __pin * k = & h -> j;

   // ...
};
```

在新的語言設計中，是使用類似的內部指標的語法來宣告 pin 指標。

```
ref struct H
{
public:
   int j;
};

int main()
{
   H^ h = gcnew H;
   pin_ptr<int> k = &h->j;

   // ...
}
```

在新語法中的 pin 指標是特殊案例的內部指標。 保留 pin 指標的原始條件約束。 比方說，它不能做為參數或傳回類型的方法;它可以只在本機的物件上宣告。 一些其他的條件約束，不過，已加入新的語法中。

Pin 指標的預設值是`nullptr`，而非`0`。 A`pin_ptr<>`無法初始化或指派`0`。 所有的工作分派`0`在現有的程式碼必須變更為`nullptr`。

若要解決整個物件，如下列範例取自 Managed Extensions 規格允許 Managed Extensions 的 pin 指標：

```
__gc class G {
public:
   void incr(int* pi) { pi += 1; }
};
__gc struct H { int j; };
void f( G * g ) {
   H __pin * pH = new H;
   g->incr(& pH -> j);
};
```

在新語法中，釘選整個物件傳回`new`不支援運算式。 而是必須釘選內部成員的位址。 例如，套用至物件的

```
ref class G {
public:
   void incr(int* pi) { *pi += 1; }
};
ref struct H { int j; };
void f( G^ g ) {
   H ^ph = gcnew H;
   Console::WriteLine(ph->j);
   pin_ptr<int> pj = &ph->j;
   g->incr(  pj );
   Console::WriteLine(ph->j);
}
```

## <a name="see-also"></a>另請參閱

[實值型別及其行為 (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
[類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)<br/>
[interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)<br/>
[pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)