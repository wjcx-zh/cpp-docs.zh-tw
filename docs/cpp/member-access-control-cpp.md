---
title: "成員存取控制 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- access control [C++]
- member access [C++]
- member-access control [C++]
ms.assetid: 2d596bca-56ad-4277-94e1-ce3db45fa14a
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 4d209e8f5e00460f1183a154f90bbdafd459b755
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="member-access-control-c"></a>成員存取控制 (C++)
存取控制可讓您區隔[公用](../cpp/public-cpp.md)介面的類別，以從[私人](../cpp/private-cpp.md)實作詳細資料和[保護](../cpp/protected-cpp.md)成員只使用在衍生的類別。 除非發現下一個存取規範，否則存取規範會套用至在其後宣告的所有成員。  
  
```  
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
  
 預設存取權是類別中的 `private` 以及 結構或等位中的 `public` 您可以依任意順序使用類別中的存取規範任何次數。 類別類型物件的儲存配置依實作而定，不過，成員一定會具有存取指定名稱之間指派的後續較高之記憶體位址。  
  
### <a name="member-access-control"></a>成員存取控制  
  
|存取的類型|意義|  
|--------------------|-------------|  
|[private](../cpp/private-cpp.md)|只有成員函式和類別的 friend (類別或函式) 可以使用宣告為 `private` 的類別成員。|  
|[protected](../cpp/protected-cpp.md)|成員函式和類別的 friend (類別或函式) 可以使用宣告為 `protected` 的類別成員。 此外，類別所衍生的類別也可以使用這些類別成員。|  
|[public](../cpp/public-cpp.md)|類別成員宣告為**公用**可供任何函式。|  
  
 存取控制有助於避免您誤用物件。 執行明確類型轉換 (轉型) 時，會失去這項保護。  
  
> [!NOTE]
>  存取控制同樣適用於所有名稱：成員函式、成員資料、巢狀類別及列舉程式。  
  
## <a name="access-control-in-derived-classes"></a>衍生類別中的存取控制  
 在衍生類別中可存取哪些基底類別的成員是由兩個因素所控制，這些相同的因素可控制在衍生類別中對於繼承成員的存取：  
  
-   在衍生的類別是否宣告基底類別使用**公用**存取規範中的*類別標頭*(*類別標頭*的文法>一節所述[定義類別類型](http://msdn.microsoft.com/en-us/e8c65425-0f3a-4dca-afc2-418c3b1e57da))。  
  
-   要存取哪些基底類別的成員。  
  
 下表顯示這些因素之間的互動，以及如何判斷基底類別成員存取。  
  
### <a name="member-access-in-base-class"></a>基底類別中的成員存取  
  
|private|protected|Public|  
|-------------|---------------|------------|  
|永遠無法存取，不論衍生存取為何|如果使用 private 衍生，則可存取衍生類別中的 private 成員|如果使用 private 衍生，則可存取衍生類別中的 private 成員|  
||如果使用 protected 衍生，則可存取衍生類別中的 protected 成員|如果使用 protected 衍生，則可存取衍生類別中的 protected 成員|  
||如果使用 public 衍生，則可存取衍生類別中的 Protected 成員|如果使用 public 衍生，則可存取衍生類別中的 Public 成員|  
  
 下面這個範例可說明這點：  
  
```  
// access_specifiers_for_base_classes.cpp  
class BaseClass  
{  
public:  
    int PublicFunc();    // Declare a public member.  
protected:  
    int ProtectedFunc(); // Declare a protected member.  
private:  
    int PrivateFunc();   // Declare a private member.  
};  
  
// Declare two classes derived from BaseClass.  
class DerivedClass1 : public BaseClass  
{  
};  
  
class DerivedClass2 : private BaseClass  
{  
};  
  
int main()  
{  
}  
```  
  
 在 `DerivedClass1` 中，成員函式 `PublicFunc` 是 public 成員，而 `ProtectedFunc` 是 protected 成員，因為 `BaseClass` 是 public 基底類別。 `PrivateFunc` 對 `BaseClass` 而言是 private，且無法存取任何衍生類別。  
  
 在 `DerivedClass2` 中，因為 `PublicFunc` 是 private 基底類別，因此會將函式 `ProtectedFunc` 和 `BaseClass` 視為是 private 成員。 同樣地，`PrivateFunc` 對 `BaseClass` 而言是 private，且無法存取任何衍生類別。  
  
 您可以在未使用基底類別存取指定名稱的情況下宣告衍生類別。 在這種情況下，衍生視為 private 如果衍生的類別宣告使用**類別**關鍵字。 如果衍生類別宣告使用 `struct` 關鍵字，則會將該衍生視為 public。 例如，下列程式碼：  
  
```  
class Derived : Base  
...  
```  
  
 等於：  
  
```  
class Derived : private Base  
...  
```  
  
 同樣地，下列程式碼：  
  
```  
struct Derived : Base  
...  
```  
  
 等於：  
  
```  
struct Derived : public Base  
...  
```  
  
 請注意，宣告為具有 private 存取權限的成員無法存取函式或衍生類別，除非那些函式或類別在基底類別中是使用 `friend` 宣告加以宣告。  
  
 A **union**類型不能有基底類別。  
  
> [!NOTE]
>  指定 private 基底類別時，建議明確使用 `private` 關鍵字加以指定，讓衍生類別的使用者能夠了解成員存取。  
  
## <a name="access-control-and-static-members"></a>存取控制和靜態成員  
 當您將基底類別指定為 `private` 時，只會影響到非靜態成員。 在衍生類別中仍然可以存取公用的靜態成員。 不過，使用指標、參考或物件存取基底類別的成員可能需要進行轉換，此時會重新套用存取控制。 參考下列範例：  
  
```  
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
  
 在上述程式碼中，存取控制項禁止從 `Derived2` 的指標轉換為 `Base` 的指標。 **這**指標可以隱含轉換為型別`Derived2 *`。 若要選取`CountOf`函式，**這**必須轉換成輸入`Base *`。 由於 `Base` 是 `Derived2` 的私用間接基底類別，因此不允許進行這類轉換。 只有直接衍生類別的指標可以轉換為私用的基底類別類型。 因此，`Derived1 *` 類型的指標可以轉換成 `Base *` 類型。  
  
 請注意，明確呼叫 `CountOf` 函式，而不使用指標、參考或物件加以選取，表示沒有進行轉換。 因此，可以進行呼叫。  
  
 衍生類別的成員和 friend (即 `T`) 可以將 `T` 的指標轉換為 `T` 的私用直接基底類別的指標。  
  
## <a name="access-to-virtual-functions"></a>存取虛擬函式  
 存取控制套用至[虛擬](../cpp/virtual-cpp.md)函式由用來進行呼叫的函式的類型。 覆寫函式的宣告不會影響特定類型的存取控制。 例如:  
  
```  
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
>  虛擬函式 `GetState` 可以使用基底類別 `VFuncBase`的指標呼叫。 這並不表示呼叫的函式是該函式的基底類別版本。  
  
## <a name="access-control-with-multiple-inheritance"></a>具有多重繼承的存取控制  
 在包含虛擬基底類別的多重繼承斜格紋中，可以透過多個路徑存取指定的名稱。 由於可以依循這些不同路徑套用不同的存取控制，編譯器會選擇授予較多存取權的路徑。 請參閱下圖。  
  
 ![依序繼承圖形的路徑進行存取](../cpp/media/vc38v91.gif "vc38V91")  
依序繼承圖形的路徑進行存取  
  
 在圖中，類別 `VBase` 中宣告的名稱一定會透過類別 `RightPath` 進行存取。 正確的路徑會更容易存取，因為 `RightPath` 會將 `VBase` 宣告為公用基底類別，`LeftPath` 則是將 `VBase` 宣告為私用。  
  
## <a name="see-also"></a>另請參閱  
 [C++ 語言參考](../cpp/cpp-language-reference.md)
