---
title: 用為實值型別的 C++ 類別
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: f63bb62c-60da-40d5-ac14-4366608fe260
ms.openlocfilehash: 1aabcad46e848e1a499a142adaba5002a829bbf5
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246013"
---
# <a name="c-classes-as-value-types"></a>用為實值型別的 C++ 類別

C++類別預設為實數值型別。 您可以將它們指定為參考型別，讓多型行為能夠支援物件導向程式設計。 數值型別有時可以從記憶體和版面配置控制項的角度來查看，而參考型別則是關於基類和虛擬函式，以進行多型的用途。 根據預設，實值型別為可複製，這表示一定會有複製的函式和複製指派運算子。 針對參考型別，您可以將類別設為非可複製（停用複製程式設計函數和複製指派運算子），並使用支援其所需多型的虛擬析構函式。 實值型別也是內容的相關資訊，當複製它們時，一律會提供兩個獨立的值供您分別修改。 參考型別是關於身分識別-這是什麼類型的物件？ 因此，「參考型別」也稱為「多型類型」。

如果您真的想要類似參考的型別（基類、虛擬函式），您必須明確停用複製，如下列程式碼中的 `MyRefType` 類別所示。

```cpp
// cl /EHsc /nologo /W4

class MyRefType {
private:
    MyRefType & operator=(const MyRefType &);
    MyRefType(const MyRefType &);
public:
    MyRefType () {}
};

int main()
{
    MyRefType Data1, Data2;
    // ...
    Data1 = Data2;
}
```

編譯上述程式碼將會產生下列錯誤：

```Output
test.cpp(15) : error C2248: 'MyRefType::operator =' : cannot access private member declared in class 'MyRefType'
        meow.cpp(5) : see declaration of 'MyRefType::operator ='
        meow.cpp(3) : see declaration of 'MyRefType'
```

## <a name="value-types-and-move-efficiency"></a>實數值型別和移動效率

由於新的複製優化，因此可避免複製配置額外負荷。 例如，當您在字串向量的中間插入字串時，將不會有任何複製重新配置額外負荷，只有移動-即使它導致向量本身增加也一樣。 這也適用于其他作業，例如在兩個非常大型的物件上執行 add 運算。 如何啟用這些值作業優化？ 在某些C++編譯器中，編譯器會隱含地為您啟用此功能，就像複製函式可以由編譯器自動產生一樣。 不過，在C++中，您的類別必須在類別定義中宣告，以「加入宣告」來移動指派和函數。 在適當的成員函式宣告中使用 double 符號（& &）右值參考，並定義移動函數和移動指派方法，即可完成這項作業。  您也必須插入正確的程式碼，以「竊取 getmembers」來源物件。

您要如何決定是否需要啟用移動？ 如果您已經知道您需要啟用「複製結構」，您可能會想要在可能比深層複本更便宜的情況下，啟用移動。 不過，如果您知道需要移動支援，則不一定表示您想要啟用複製。 第二種情況則稱為「僅限移動類型」。 標準程式庫中已有一個範例 `unique_ptr`。 請注意，舊的 `auto_ptr` 已被取代，而且已 `unique_ptr` 精確地取代，因為舊版中缺少 move 語義支援C++。

藉由使用移動語義，您可以傳回傳值或插入中間。 Move 是複製的優化。 需要堆積配置做為因應措施。 請考慮下列虛擬程式碼：

```cpp
#include <set>
#include <vector>
#include <string>
using namespace std;

//...
set<widget> LoadHugeData() {
    set<widget> ret;
    // ... load data from disk and populate ret
    return ret;
}
//...
widgets = LoadHugeData();   // efficient, no deep copy

vector<string> v = IfIHadAMillionStrings();
v.insert( begin(v)+v.size()/2, "scott" );   // efficient, no deep copy-shuffle
v.insert( begin(v)+v.size()/2, "Andrei" );  // (just 1M ptr/len assignments)
//...
HugeMatrix operator+(const HugeMatrix& , const HugeMatrix& );
HugeMatrix operator+(const HugeMatrix& ,       HugeMatrix&&);
HugeMatrix operator+(      HugeMatrix&&, const HugeMatrix& );
HugeMatrix operator+(      HugeMatrix&&,       HugeMatrix&&);
//...
hm5 = hm1+hm2+hm3+hm4+hm5;   // efficient, no extra copies
```

### <a name="enabling-move-for-appropriate-value-types"></a>啟用適用于適當數值型別的移動

針對類似值的類別，移動可以比深層複本便宜，針對效率啟用移動結構和移動指派。 請考慮下列虛擬程式碼：

```cpp
#include <memory>
#include <stdexcept>
using namespace std;
// ...
class my_class {
    unique_ptr<BigHugeData> data;
public:
    my_class( my_class&& other )   // move construction
        : data( move( other.data ) ) { }
    my_class& operator=( my_class&& other )   // move assignment
    { data = move( other.data ); return *this; }
    // ...
    void method() {   // check (if appropriate)
        if( !data )
            throw std::runtime_error("RUNTIME ERROR: Insufficient resources!");
    }
};
```

如果您啟用 [複製結構/指派]，也可以啟用 [移動結構/指派] （如果它比深層複本便宜）。

某些*非實值*類型為僅限移動，例如當您無法複製資源時，只會傳送擁有權。 範例：`unique_ptr`。

## <a name="see-also"></a>另請參閱

[C++類型系統](../cpp/cpp-type-system-modern-cpp.md)<br/>
[歡迎回到C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)
