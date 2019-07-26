---
title: vector&lt;bool&gt; 類別
ms.date: 11/04/2016
f1_keywords:
- vector<bool>
- vector/std::vector::const_pointer
- vector/std::vector::const_reference
- vector/std::vector::pointer
- vector/std::vector::flip
- vector/std::vector::swap
helpviewer_keywords:
- std::vector [C++], const_pointer
- std::vector [C++], const_reference
- std::vector [C++], pointer
- std::vector [C++], flip
- std::vector [C++], swap
ms.assetid: 8028c8ed-ac9c-4f06-aba1-5de45c00aafb
ms.openlocfilehash: d4ae53f9a14f04d5656a13c32e75494688c5cdd0
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452261"
---
# <a name="vectorltboolgt-class"></a>vector&lt;bool&gt; 類別

類別是**bool**類型專案之 vector 的部分特製化。 [](../standard-library/vector-class.md) `vector<bool>` 它具有特殊化所使用之基礎類型的配置器, 它會藉由儲存每位一個**bool**值, 來提供空間優化。

## <a name="syntax"></a>語法

```cpp
template <class Allocator = allocator<bool>>
class vector<bool, Allocator>
```

## <a name="remarks"></a>備註

這個類別範本特製化的行為就像 vector，除了在本文中說明的差異之外。

處理**bool**類型的作業會對應到容器儲存體中的值。 `allocator_traits::construct` 不用來建構這些值。

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[const_pointer](#const_pointer)|`const_iterator` 的 typedef，可做為常數指標指向 `vector<bool>` 的布林值項目。|
|[const_reference](#const_reference)|**Bool**的 typedef。 在初始化之後，就無法觀察原始值的更新。|
|[pointer](#pointer)|`iterator` 的 typedef，可做為指標指向 `vector<bool>` 的布林值項目。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[flip](#flip)|會反轉 `vector<bool>` 中的所有位元。|
|[swap](#swap)|交換兩個 `vector<bool>` 的項目。|
|[operator&#91;&#93;](#op_at)|傳回在指定位置上 `vector<bool>` 項目的模擬參考。|
|`at`|作用與非特製化的 [vector](../standard-library/vector-class.md)::at 函式相同，不過，它使用 Proxy 類別 [vector\<bool>::reference](#reference_class)。 另請參閱 [operator&#91;&#93;](#op_at)。|
|`front`|作用與非特製化的 [vector](../standard-library/vector-class.md)::front 函式相同，不過，它使用 Proxy 類別 [vector\<bool>::reference](#reference_class)。 另請參閱 [operator&#91;&#93;](#op_at)。|
|`back`|作用與非特製化的 [vector](../standard-library/vector-class.md)::back 函式相同，不過，它使用 Proxy 類別 [vector\<bool>::reference](#reference_class)。 另請參閱 [operator&#91;&#93;](#op_at)。|

### <a name="proxy-class"></a>Proxy 類別

|||
|-|-|
|[vector\<bool> reference 類別](#reference_class)|類別，做為 Proxy 以模擬 `bool&` 行為，而且其物件可以提供對 `vector<bool>` 物件中項目 (單一位元) 的參考。|

## <a name="requirements"></a>需求

**標頭**：\<vector>

**命名空間：** std

## <a name="const_pointer"></a>  vector\<bool>::const_pointer

類型，描述可以做為常數指標的物件，指向由 `vector<bool>` 物件所包含序列的布林值項目。

```cpp
typedef const_iterator const_pointer;
```

## <a name="const_reference"></a>  vector\<bool>::const_reference

類型，描述可以做為常數參考的物件，指向由 `vector<bool>` 物件所包含序列的布林值項目。

```cpp
typedef bool const_reference;
```

### <a name="remarks"></a>備註

如需詳細資訊和程式碼範例，請參閱 [vector&lt;bool&gt;::reference::operator=](#reference_operator_eq)。

## <a name="flip"></a>  vector\<bool>::flip

會反轉 `vector<bool>` 中的所有位元。

```cpp
void flip();
```

### <a name="example"></a>範例

```cpp
// vector_bool_flip.cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha; // format output for subsequent code

    vector<bool> vb = { true, false, false, true, true };
    cout << "The vector is:" << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;

    vb.flip();

    cout << "The flipped vector is:" << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;
}
```

## <a name="op_at"></a>  vector\<bool>::operator[]

傳回在指定位置上 `vector<bool>` 項目的模擬參考。

```cpp
vector<bool>::reference operator[](size_type Pos);

vector&<bool&>::const_reference operator[](size_type Pos) const;
```

### <a name="parameters"></a>參數

|參數|說明|
|-|-|
|*採購*|`vector<bool>` 項目的位置。|

### <a name="return-value"></a>傳回值

[vector\<bool>::reference](#reference_class) 或 [vector\<bool>::const_reference](#const_reference) 物件，包含索引項目的值。

如果指定的位置大於或等於容器大小，則結果是未定義。

### <a name="remarks"></a>備註

如果您使用 _ITERATOR_DEBUG_LEVEL 集進行編譯, 如果您嘗試存取向量界限以外的元素, 就會發生執行階段錯誤。  如需詳細資訊，請參閱 [Checked Iterators](../standard-library/checked-iterators.md)。

### <a name="example"></a>範例

這個程式碼範例會示範 `vector<bool>::operator[]` 的正確用法和兩個常見的程式碼錯誤 (已標記為註解)。這些會造成錯誤，因為 `vector<bool>::reference` 所傳回 `vector<bool>::operator[]` 物件的位址無法採用。

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha;
    vector<bool> vb;

    vb.push_back(true);
    vb.push_back(false);

    //    bool* pb = &vb[1]; // conversion error - do not use
    //    bool& refb = vb[1];   // conversion error - do not use
    bool hold = vb[1];
    cout << "The second element of vb is " << vb[1] << endl;
    cout << "The held value from the second element of vb is " << hold << endl;

    // Note this doesn't modify hold.
    vb[1] = true;
    cout << "The second element of vb is " << vb[1] << endl;
    cout << "The held value from the second element of vb is " << hold << endl;
}
```

## <a name="pointer"></a>  vector\<bool>::pointer

類型，描述可以做為指標的物件，指向由 `vector<bool>` 物件所包含序列的布林值項目。

```cpp
typedef iterator pointer;
```

## <a name="reference_class"></a>  vector\<bool>::reference Class

`vector<bool>::reference` 類別是 [vector\<bool> 類別](../standard-library/vector-bool-class.md)提供的 Proxy 類別，用來模擬 `bool&`。

### <a name="remarks"></a>備註

需要模擬參考，因為 C++ 原生不允許對位元的直接參考。 `vector<bool>` 對每個項目只使用一個位元，您可以使用這個 Proxy 類別來參考位元。 不過，因為某些指派無效，參考模擬不完整。 例如，因為 `vector<bool>::reference` 物件位址無法採用，使用 [vector\<bool>::operator&#91;&#93;](#op_at) 的下列程式碼不正確：

```cpp
vector<bool> vb;
//...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

###  <a name="reference_flip"></a>  vector\<bool>::reference::flip

反轉所參考 [vector\<bool>](../standard-library/vector-bool-class.md) 項目的布林值。

```cpp
void flip();
```

#### <a name="example"></a>範例

```cpp
// vector_bool_ref_flip.cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha;

    vector<bool> vb = { true, false, false, true, true };

    cout << "The vector is: " << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;

    vector<bool>::reference vbref = vb.front();
    vbref.flip();

    cout << "The vector with first element flipped is: " << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;
}
```

```Output
The vector is:
    true false false true true
The vector with first element flipped is:
    false false false true true
```

###  <a name="reference_operator_bool"></a>  vector\<bool>::reference::operator bool

提供從`vector<bool>::reference`到**bool**的隱含轉換。

```cpp
operator bool() const;
```

#### <a name="return-value"></a>傳回值

vector\<bool> 物件項目的布林值。

#### <a name="remarks"></a>備註

這個運算子無法修改 `vector<bool>` 物件。

###  <a name="reference_operator_eq"></a>  vector\<bool>::reference::operator=

將布林值指派給位元，或是將參考的項目所表示的值指派給位元。

```cpp
reference& operator=(const reference& Right);
reference& operator=(bool Val);
```

### <a name="parameters"></a>參數

*再*\
值會指派給位元的項目參考。

*初始值*\
要指派給位元的布林值。

#### <a name="example"></a>範例

```cpp
// vector_bool_ref_op_assign.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    cout << boolalpha;

    vector<bool> vb = { true, false, false, true, true };

    print("The vector is: ", vb);

    // Invoke vector<bool>::reference::operator=()
    vector<bool>::reference refelem1 = vb[0];
    vector<bool>::reference refelem2 = vb[1];
    vector<bool>::reference refelem3 = vb[2];

    bool b1 = refelem1;
    bool b2 = refelem2;
    bool b3 = refelem3;
    cout << "The original value of the 1st element stored in a bool: " << b1 << endl;
    cout << "The original value of the 2nd element stored in a bool: " << b2 << endl;
    cout << "The original value of the 3rd element stored in a bool: " << b3 << endl;
    cout << endl;

    refelem2 = refelem1;

    print("The vector after assigning refelem1 to refelem2 is now: ", vb);

    refelem3 = true;

    print("The vector after assigning false to refelem1 is now: ", vb);

    // The initial values are still stored in the bool variables and remained unchanged
    cout << "The original value of the 1st element still stored in a bool: " << b1 << endl;
    cout << "The original value of the 2nd element still stored in a bool: " << b2 << endl;
    cout << "The original value of the 3rd element still stored in a bool: " << b3 << endl;
    cout << endl;
}
```

```Output
The vector is: true false false true true
The original value of the 1st element stored in a bool: true
The original value of the 2nd element stored in a bool: false
The original value of the 3rd element stored in a bool: false

The vector after assigning refelem1 to refelem2 is now: true true false true true
The vector after assigning false to refelem1 is now: true true true true true
The original value of the 1st element still stored in a bool: true
The original value of the 2nd element still stored in a bool: false
The original value of the 3rd element still stored in a bool: false
```

## <a name="swap"></a>  vector\<bool>::swap

靜態成員函式，透過使用 Proxy 類別 [vector\<bool>::reference](#reference_class)，交換布林值向量 (`vector<bool>`) 的兩個項目。

```cpp
static void swap(
    reference Left,
    reference Right);
```

### <a name="parameters"></a>參數

*左面*\
要與*右*元素交換的元素。

*再*\
要與*左*元素交換的元素。

### <a name="remarks"></a>備註

這個多載支援 `vector<bool>` 的特別 Proxy 需求。 [vector](../standard-library/vector-class.md)::swap 功能與 `vector<bool>::swap()` 的單一引數多載相同。

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
