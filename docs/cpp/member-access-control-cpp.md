---
title: 成員存取控制 (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- access control [C++]
- member access [C++]
- member-access control [C++]
ms.assetid: 2d596bca-56ad-4277-94e1-ce3db45fa14a
ms.openlocfilehash: e8f62e82ebb7fcc18be5ac7d203df0fb46c9b635
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369842"
---
# <a name="member-access-control-c"></a>成員存取控制 (C++)

訪問控制項使您能夠將類[的公共](../cpp/public-cpp.md)介面與[專用](../cpp/private-cpp.md)實現詳細資訊和僅供派生類使用的[受保護](../cpp/protected-cpp.md)成員分開。 除非發現下一個存取規範，否則存取規範會套用至在其後宣告的所有成員。

```cpp
class Point
{
public:
    Point( int, int ) // Declare public constructor.;
    Point();// Declare public default constructor.
    int &x( int ); // Declare public accessor.
    int &y( int ); // Declare public accessor.

private:                 // Declare private state variables.
    int _x;
    int _y;

protected:      // Declare protected function for derived classes only.
    Point ToWindowCoords();
};
```

默認訪問在類中是**私有**的,並且在結構或聯合中**是公共**的。 您可以依任意順序使用類別中的存取規範任何次數。 類別類型物件的儲存配置依實作而定，不過，成員一定會具有存取指定名稱之間指派的後續較高之記憶體位址。

## <a name="member-access-control"></a>成員存取控制

|存取的類型|意義|
|--------------------|-------------|
|[私人](../cpp/private-cpp.md)|聲明為**私有**的類成員只能由類的成員函數和好友(類或函數)使用。|
|[protected](../cpp/protected-cpp.md)|聲明為**受保護**的類成員可以由類的成員函數和好友(類或函數)使用。 此外，類別所衍生的類別也可以使用這些類別成員。|
|[public](../cpp/public-cpp.md)|聲明為**公共**的類成員可以由任何函數使用。|

存取控制有助於避免您誤用物件。 執行明確類型轉換 (轉型) 時，會失去這項保護。

> [!NOTE]
> 存取控制同樣適用於所有名稱：成員函式、成員資料、巢狀類別及列舉程式。

## <a name="access-control-in-derived-classes"></a>衍生類別中的存取控制

在衍生類別中可存取哪些基底類別的成員是由兩個因素所控制，這些相同的因素可控制在衍生類別中對於繼承成員的存取：

- 派生類是否使用**公共**訪問指定器聲明基類。

- 要存取哪些基底類別的成員。

下表顯示這些因素之間的互動，以及如何判斷基底類別成員存取。

### <a name="member-access-in-base-class"></a>基底類別中的成員存取

|private|protected|公開|
|-------------|---------------|------------|
|永遠無法存取，不論衍生存取為何|如果使用 private 衍生，則可存取衍生類別中的 private 成員|如果使用 private 衍生，則可存取衍生類別中的 private 成員|
||如果使用 protected 衍生，則可存取衍生類別中的 protected 成員|如果使用 protected 衍生，則可存取衍生類別中的 protected 成員|
||如果使用 public 衍生，則可存取衍生類別中的 Protected 成員|如果使用 public 衍生，則可存取衍生類別中的 Public 成員|

下列範例會加以說明：

```cpp
// access_specifiers_for_base_classes.cpp
class BaseClass
{
public:
    int PublicFunc(); // Declare a public member.
protected:
    int ProtectedFunc(); // Declare a protected member.
private:
    int PrivateFunc(); // Declare a private member.
};

// Declare two classes derived from BaseClass.
class DerivedClass1 : public BaseClass
{
    void foo()
    {
        PublicFunc();
        ProtectedFunc();
        PrivateFunc(); // function is inaccessible
    }
};

class DerivedClass2 : private BaseClass
{
    void foo()
    {
        PublicFunc();
        ProtectedFunc();
        PrivateFunc(); // function is inaccessible
    }
};

int main()
{
    DerivedClass1 derived_class1;
    DerivedClass2 derived_class2;
    derived_class1.PublicFunc();
    derived_class2.PublicFunc(); // function is inaccessible
}
```

在 `DerivedClass1` 中，成員函式 `PublicFunc` 是 public 成員，而 `ProtectedFunc` 是 protected 成員，因為 `BaseClass` 是 public 基底類別。 `PrivateFunc` 對 `BaseClass` 而言是 private，且無法存取任何衍生類別。

在 `DerivedClass2` 中，因為 `PublicFunc` 是 private 基底類別，因此會將函式 `ProtectedFunc` 和 `BaseClass` 視為是 private 成員。 同樣地，`PrivateFunc` 對 `BaseClass` 而言是 private，且無法存取任何衍生類別。

您可以在未使用基底類別存取指定名稱的情況下宣告衍生類別。 在這種情況下,如果派生類聲明使用**類**關鍵字,則派生被視為私有。 如果派生類聲明使用**結構**關鍵字,則派生被視為公共。 例如，下列程式碼：

```cpp
class Derived : Base
...
```

相當於：

```cpp
class Derived : private Base
...
```

同樣地，下列程式碼：

```cpp
struct Derived : Base
...
```

相當於：

```cpp
struct Derived : public Base
...
```

請注意,聲明為具有私有訪問許可權的成員不能訪問函數或派生類,除非這些函數或類使用基類中的**frienda**聲明聲明。

**聯合**類型不能具有基類。

> [!NOTE]
> 指定私有基類時,建議顯式使用**私有**關鍵字,以便派生類的使用者了解成員訪問許可權。

## <a name="access-control-and-static-members"></a>存取控制和靜態成員

將基類指定為**私有**類時,它只影響非靜態成員。 在衍生類別中仍然可以存取公用的靜態成員。 不過，使用指標、參考或物件存取基底類別的成員可能需要進行轉換，此時會重新套用存取控制。 請考慮下列範例：

```cpp
// access_control.cpp
class Base
{
public:
    int Print();             // Nonstatic member.
    static int CountOf();    // Static member.
};

// Derived1 declares Base as a private base class.
class Derived1 : private Base
{
};
// Derived2 declares Derived1 as a public base class.
class Derived2 : public Derived1
{
    int ShowCount();    // Nonstatic member.
};
// Define ShowCount function for Derived2.
int Derived2::ShowCount()
{
   // Call static member function CountOf explicitly.
    int cCount = Base::CountOf();     // OK.

   // Call static member function CountOf using pointer.
    cCount = this->CountOf();  // C2247. Conversion of
                               //  Derived2 * to Base * not
                               //  permitted.
    return cCount;
}
```

在上述程式碼中，存取控制項禁止從 `Derived2` 的指標轉換為 `Base` 的指標。 **這個**指標是隱式型態`Derived2 *`。 要選擇函數`CountOf`,必須**將轉換**為類型`Base *`。 由於 `Base` 是 `Derived2` 的私用間接基底類別，因此不允許進行這類轉換。 只有直接衍生類別的指標可以轉換為私用的基底類別類型。 因此，`Derived1 *` 類型的指標可以轉換成 `Base *` 類型。

請注意，明確呼叫 `CountOf` 函式，而不使用指標、參考或物件加以選取，表示沒有進行轉換。 因此，可以進行呼叫。

衍生類別的成員和 friend (即 `T`) 可以將 `T` 的指標轉換為 `T` 的私用直接基底類別的指標。

## <a name="access-to-virtual-functions"></a>存取虛擬函式

應用於[虛擬](../cpp/virtual-cpp.md)函數的訪問控制由用於進行函數調用的類型確定。 覆寫函式的宣告不會影響特定類型的存取控制。 例如：

```cpp
// access_to_virtual_functions.cpp
class VFuncBase
{
public:
    virtual int GetState() { return _state; }
protected:
    int _state;
};

class VFuncDerived : public VFuncBase
{
private:
    int GetState() { return _state; }
};

int main()
{
   VFuncDerived vfd;             // Object of derived type.
   VFuncBase *pvfb = &vfd;       // Pointer to base type.
   VFuncDerived *pvfd = &vfd;    // Pointer to derived type.
   int State;

   State = pvfb->GetState();     // GetState is public.
   State = pvfd->GetState();     // C2248 error expected; GetState is private;
}
```

在上述範例中，使用 `GetState` 類型的指標呼叫虛擬函式 `VFuncBase` 會呼叫 `VFuncDerived::GetState`，而 `GetState` 會視為 Public。 不過，使用 `GetState` 類型的指標呼叫 `VFuncDerived` 會發生存取控制違規，因為 `GetState` 在 `VFuncDerived` 類別中宣告為 Private。

> [!CAUTION]
> 虛擬函式 `GetState` 可以使用基底類別 `VFuncBase`的指標呼叫。 這並不表示呼叫的函式是該函式的基底類別版本。

## <a name="access-control-with-multiple-inheritance"></a>具有多重繼承的存取控制

在包含虛擬基底類別的多重繼承斜格紋中，可以透過多個路徑存取指定的名稱。 由於可以依循這些不同路徑套用不同的存取控制，編譯器會選擇授予較多存取權的路徑。 請參閱下圖。

![依序繼承圖形的路徑進行存取](../cpp/media/vc38v91.gif "依序繼承圖形的路徑進行存取") <br/>
依序繼承圖形的路徑進行存取

在圖中，類別 `VBase` 中宣告的名稱一定會透過類別 `RightPath` 進行存取。 正確的路徑會更容易存取，因為 `RightPath` 會將 `VBase` 宣告為公用基底類別，`LeftPath` 則是將 `VBase` 宣告為私用。

## <a name="see-also"></a>另請參閱

[C++語言參考](../cpp/cpp-language-reference.md)
