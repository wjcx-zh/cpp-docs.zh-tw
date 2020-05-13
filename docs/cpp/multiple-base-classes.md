---
title: 多個基底類別
ms.date: 11/19/2018
helpviewer_keywords:
- base classes [C++], multiple
- derived classes [C++], multiple bases
- multiple inheritance, class declaration
- multiple base classes [C++]
ms.assetid: a30c69fe-401c-4a87-96a0-e0da70c7c740
ms.openlocfilehash: 7cac70da5dd7093ce3e9c1cf3d2350d780c6b391
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353726"
---
# <a name="multiple-base-classes"></a>多個基底類別

類可以從多個基類派生。 在多繼承模型中(類派生自多個基類),使用*基清單*語法元素指定基類。 例如，可以指定衍生自 `CollectionOfBook` 和 `Collection` 的 `Book` 類別宣告：

```cpp
// deriv_MultipleBaseClasses.cpp
// compile with: /LD
class Collection {
};
class Book {};
class CollectionOfBook : public Book, public Collection {
    // New members
};
```

除非是在叫用建構函式和解構函式的特定情況下，否則指定基底類別的順序並不重要。 在這些情況下，指定基底類別的順序會影響下列各項：

- 建構函式進行初始化的順序。 如果程式碼要求 `Book` 的 `CollectionOfBook` 部分必須在 `Collection` 部分之前初始化，則指定的順序就很重要。 初始化按在*基清單中*指定的類的順序進行。

- 叫用解構函式進行清除的順序。 同樣地，如果類別的特定「部分」必須在其他部分終結時存在，則順序就很重要。 析構函數按*基清單*中指定的類的相反順序調用。

    > [!NOTE]
    >  基底類別的指定順序可能會影響類別的記憶體配置。 請不要依據記憶體中基底成員的順序做出任何程式設計上的決策。

指定*基清單*時,不能多次指定同一類名。 不過，類別可以多次做為衍生類別的間接基底。

## <a name="virtual-base-classes"></a>虛擬基底類別

由於類別可以多次做為衍生類別的間接基底類別，因此 C++ 針對此類的基底類別工作提供一種最佳化的方式。 虛擬基底類別可節省空間，並在使用多重繼承的類別階層架構時避免出現模稜兩可的問題。

每個非虛擬物件都包含基底類別中定義的資料成員。 重複項目不僅佔用空間，您還必須在存取時指定您需要的基底類別成員複本。

將基底類別指定為虛擬基底類別時，可多次將其當做間接基底，而不需要使用其資料成員的複本。 其資料成員的單一複本會由所有基底類別共用 (這些類別會將其當做虛擬基底使用)。

宣告虛擬基類別時,**虛擬**關鍵字會顯示在派生類的基本清單中。

考慮下圖中的類別階層架構，其中示範模擬的午餐供應線。

![模擬的午餐流程圖形](../cpp/media/vc38xp1.gif "模擬的午餐流程圖形") <br/>
類比午餐線圖

在圖中，`Queue` 為 `CashierQueue` 和 `LunchQueue` 的基底類別。 不過，在將這兩個類別合併為 `LunchCashierQueue` 時會發生下列問題：新的類別會內含兩個來自 `Queue` 類型的子物件，其中一個來自 `CashierQueue`，另一個則是來自 `LunchQueue`。 下圖顯示概念性的記憶體配置 (實際的記憶體配置可能會進行最佳化)。

![類比午餐&#45;線物件](../cpp/media/vc38xp2.gif "類比午餐&#45;線物件") <br/>
模擬的午餐流程物件

請注意，`Queue` 物件中有兩個 `LunchCashierQueue` 子物件。 下列程式碼會將 `Queue` 宣告為虛擬基底類別：

```cpp
// deriv_VirtualBaseClasses.cpp
// compile with: /LD
class Queue {};
class CashierQueue : virtual public Queue {};
class LunchQueue : virtual public Queue {};
class LunchCashierQueue : public LunchQueue, public CashierQueue {};
```

**虛擬**關鍵字確保僅包含子物件`Queue`的 一個副本(請參見下圖)。

![類比午餐&#45;線物件、虛擬基類](../cpp/media/vc38xp3.gif "類比午餐&#45;線物件、虛擬基類") <br/>
具有虛擬基類別的類比的午餐線物件

一個類別可以擁有一個虛擬元件和一個特定類型的非虛擬元件。 此情況會發生在如下圖中示範的情況下。

![類別虛擬和非&#45;虛擬元件](../cpp/media/vc38xp4.gif "類別虛擬和非&#45;虛擬元件") <br/>
同一類的虛擬和非虛擬元件

在圖中，`CashierQueue` 和 `LunchQueue` 使用 `Queue` 做為虛擬基底類別。 不過，`TakeoutQueue` 指定 `Queue` 做為基底類別，而不是虛擬基底類別。 因此，`LunchTakeoutCashierQueue` 內含兩個類型為 `Queue` 的子物件：一個是來自包含 `LunchCashierQueue` 的繼承路徑，另一個是來自包含 `TakeoutQueue` 的路徑。 下圖中說明此情形。

![虛擬&物件佈局中的非&#45;虛擬繼承](../cpp/media/vc38xp5.gif "虛擬&物件佈局中的非&#45;虛擬繼承") <br/>
具有虛擬和非虛擬繼承的物件佈局

> [!NOTE]
> 與使用非虛擬繼承相比較，使用虛擬繼承在大小方面提供相當大的優勢。 不過，它可能會增加額外的處理負擔。

如果衍生類別會覆寫從虛擬基底類別繼承的虛擬函式，且衍生基底類別的建構函式或解構函式使用虛擬基底類別的指標呼叫函式，編譯器可能會在內含虛擬基底的類別中採用額外的隱藏 [vtordisp] 欄位。 編譯器`/vd0`選項禁止添加隱藏的 vtordisp 構造函數/析構函數位移成員。 編譯器`/vd1`選項(預設值)可在需要的位置啟用它們。 請只有在您確定所有類別建構函式和解構函式都會實際呼叫虛擬函式時，才關閉 vtordisps。

編譯器`/vd`選項會影響整個編譯模組。 使用`vtordisp`雜注來抑制欄位,然後逐類`vtordisp`重新 啟用欄位:

```cpp
#pragma vtordisp( off )
class GetReal : virtual public { ... };
\#pragma vtordisp( on )
```

## <a name="name-ambiguities"></a>名稱語意模糊

多重繼承實現了依循多個路徑繼承名稱的可能性。 來自這些路徑的類別成員名稱不一定是唯一的。 這些名稱衝突稱為「模稜兩可」。

參考類別成員的所有運算式都必須進行明確參考。 下列範例將示範如何發展出模稜兩可的情況：

```cpp
// deriv_NameAmbiguities.cpp
// compile with: /LD
// Declare two base classes, A and B.
class A {
public:
    unsigned a;
    unsigned b();
};

class B {
public:
    unsigned a();  // Note that class A also has a member "a"
    int b();       //  and a member "b".
    char c;
};

// Define class C as derived from A and B.
class C : public A, public B {};
```

以上述類別宣告為例，下面這類程式碼就是模稜兩可，因為不清楚 `b` 是參考 `b` 還是 `A` 中的 `B`：

```cpp
C *pc = new C;

pc->b();
```

請參考上述範例。 由於名稱 `a` 同時是 `A` 類別和 `B` 類別的成員，因此編譯器無法分辨哪一個 `a` 指定要呼叫的函式。 如果成員可以參考多個函式、物件、類型或列舉程式，則對該成員的存取就是模稜兩可的情況。

編譯器會依照下列順序執行測試來偵測模稜兩可的情況：

1. 如果對名稱的存取是模稜兩可的情況 (如上所述)，則會產生錯誤訊息。

1. 如果多載函式並非模稜兩可，就會進行解析 

1. 如果對名稱的存取違反成員存取的權限，則會產生錯誤訊息  (關於詳細資訊,請參考[成員存取控制](../cpp/member-access-control-cpp.md)。

當運算式透過繼承產生模稜兩可的情況時，您可以使用類別名稱限定所指的名稱，藉此手動解析該名稱。 若要讓上述範例正確編譯而不發生模稜兩可的情況，請使用如下所示的程式碼：

```cpp
C *pc = new C;

pc->B::a();
```

> [!NOTE]
> 當 `C` 宣告時，它可能會在 `B` 於 `C` 的範圍中參考時造成錯誤。 不過，只有 `B` 範圍中實際參考未限定的 `C` 時，才會發出錯誤。

### <a name="dominance"></a>支配

透過繼承圖形可能會到達多個名稱 (函式、物件或列舉程式)。 這種情況視為與非虛擬基底類別模稜兩可。 除非其中一個名稱為其他名稱的「主要」名稱，否則它們也是視為與虛擬基底類別模稜兩可。

如果兩個類別中皆定義了該名稱，且某個類別是衍生自另一個類別，則其名稱優先於另一個名稱。 主要名稱是衍生類別中的名稱，這個名稱會在出現模稜兩可時使用，如下列範例所示：

```cpp
// deriv_Dominance.cpp
// compile with: /LD
class A {
public:
    int a;
};

class B : public virtual A {
public:
    int a();
};

class C : public virtual A {};

class D : public B, public C {
public:
    D() { a(); } // Not ambiguous. B::a() dominates A::a.
};
```

### <a name="ambiguous-conversions"></a>模稜兩可的轉換

從指標或參考明確或隱含轉換為類別類型，可能會造成模稜兩可的情況。 下圖「指標不明確地轉換為基底類別」顯示下列項目:

- 宣告類型為 `D` 的物件。

- 將運算子的位址 (**&**) 應用於該物件的效果。 請注意，傳址運算子一律會提供該物件的基底位址。

- 將使用傳址運算子取得的指標明確轉換為基底類別類型 `A` 的作用。 請注意，若強制將物件位址設為 `A*` 類型，編譯器永遠無法得到足以判斷應選取哪一個 `A` 類型之子物件的資訊；在這種情況下，會同時存在兩個子物件。

![指標不明確地轉換為基底類別](../cpp/media/vc38xt1.gif "指標不明確地轉換為基底類別") <br/>
指標不明確地轉換為基底類別

類型 `A*` (`A` 的指標) 的轉換是模稜兩可的，因為沒有辦法分辨哪一個 `A` 類型的子物件是正確的。 請注意，您可以明確指定要使用的子物件，以避免模稜兩可的情況，如下所示：

```cpp
(A *)(B *)&d       // Use B subobject.
(A *)(C *)&d       // Use C subobject.
```

### <a name="ambiguities-and-virtual-base-classes"></a>語意模糊和虛擬基底類別

如果使用虛擬基底類別，則可以透過多重繼承路徑存取函式、物件、類型和列舉值。 因為只有一個基底類別的執行個體，在存取這些名稱時不會出現模稜兩可的情形。

下圖顯示物件使用虛擬和非虛擬繼承的組成方式。

![虛擬派生和非&#45;虛擬派生](../cpp/media/vc38xr1.gif "虛擬派生和非&#45;虛擬派生") <br/>
虛擬與非虛擬派生

在圖中，透過非虛擬基底類別存取類別 `A` 的所有成員會產生模稜兩可的情況，編譯器不會提供是否要使用與 `B` 關聯的子物件，或使用與 `C` 關聯之子物件的資訊。 不過，當 `A` 指定為虛擬基底類別時，沒有存取子物件的問題。

## <a name="see-also"></a>另請參閱

[繼承](../cpp/inheritance-cpp.md)
