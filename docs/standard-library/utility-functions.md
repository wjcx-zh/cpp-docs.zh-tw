---
title: '&lt;utility&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- utility/std::exchange
- utility/std::forward
- utility/std::make_pair
- utility/std::move
- utility/std::swap
ms.assetid: b1df38cd-3a59-4098-9c81-83342eb719a4
helpviewer_keywords:
- std::exchange [C++]
- std::forward [C++]
- std::make_pair [C++]
- std::move [C++]
- std::swap [C++]
ms.openlocfilehash: 723b077500b9b741445efcd8574fb26cd53e5fc7
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854854"
---
# <a name="ltutilitygt-functions"></a>&lt;utility&gt; 函式

## <a name="asconst"></a>as_const

```cpp
template <class T> constexpr add_const_t<T>& as_const(T& t) noexcept;
template <class T> void as_const(const T&&) = delete;
```

### <a name="return-value"></a>傳回值

傳回*T*。

## <a name="declval"></a>declval

```cpp
template <class T> add_rvalue_reference_t<T> declval() noexcept;  // as unevaluated operand
```

## <a name="exchange"></a>固定匯率

**(C++14)** 指派新值給物件，並傳回其舊值。

```cpp
template <class T, class Other = T>
    T exchange(T& val, Other&& new_val)
```

### <a name="parameters"></a>參數

*val*\
將會收到 new_val 值的物件。

*new_val*\
其值會複製或移動到 val 的物件。

### <a name="remarks"></a>備註

對於複雜類型，當可以移動建構函式時，`exchange` 可避免複製舊值，如果它是暫存的物件或已移動，則可避免複製新值，以及使用任何可用的轉換指派運算子接受任何類型做為新值。 Exchange 函式與[std：： swap](../standard-library/algorithm-functions.md#swap)不同之處在于，左邊的引數不會移動或複製到右邊的引數。

### <a name="example"></a>範例

下列範例示範如何使用 `exchange`。 在真實世界中，`exchange` 最適用於複製高度耗費資源的大型物件：

```cpp
#include <utility>
#include <iostream>

using namespace std;

struct C
{
   int i;
   //...
};

int main()
{
   // Use brace initialization
   C c1{ 1 };
   C c2{ 2 };
   C result = exchange(c1, c2);
   cout << "The old value of c1 is: " << result.i << endl;
   cout << "The new value of c1 after exchange is: " << c1.i << endl;

   return 0;
}
```

```Output
The old value of c1 is: 1
The new value of c1 after exchange is: 2
```

## <a name="forward"></a>邁出

如果引數是右值或右值參考，有條件地將引數轉型為右值參考。 這會將引數的右值特性還原為轉送函式，以支援完美轉送。

```cpp
template <class Type>    // accepts lvalues
    constexpr Type&& forward(typename remove_reference<Type>::type& Arg) noexcept

template <class Type>    // accepts everything else
    constexpr Type&& forward(typename remove_reference<Type>::type&& Arg) noexcept
```

### <a name="parameters"></a>參數

*類型*\
傳入*arg*的數值型別，可能與*arg*的類型不同。 通常由轉送函式的樣板引數所決定。

*Arg*\
要轉型的引數。

### <a name="return-value"></a>傳回值

如果傳入*arg*的值原本是 rvalue 或 rvalue 的參考，則傳回*arg*的 rvalue 參考;否則，會傳回*Arg* ，而不會修改其類型。

### <a name="remarks"></a>備註

您必須指定明確的樣板引數呼叫 `forward`。

`forward` 不會轉送其引數。 相反地，如果引數原本是右值或右值參考，則透過有條件地將引數轉型為右值參考，`forward` 可讓編譯器在具備所轉送引數原始類型的知識下執行多載解析。 轉送函式引數的明顯類型可能與其原始類型不同，例如，當右值做為函式的引數，並且系結至參數名稱時。具有名稱會使其成為左值，而任何實際以 rvalue 形式存在的值，`forward` 會還原引數的右值特性。

還原引數的原始值的右值特性以進行多載解析，稱為「*完美轉送*」。 完美轉送讓樣板函式接受任何參考類型的引數，並在正確的多載解析需要時還原它的右值特性。 透過完美轉送，您可以保存右值的移動語意，避免必須為只變更其引數參考類型的函式提供多載。

## <a name="from_chars"></a>from_chars

```cpp
from_chars_result from_chars(const char* first, const char* last, see below& value, int base = 10);

from_chars_result from_chars(const char* first, const char* last, float& value, chars_format fmt = chars_format::general); 

from_chars_result from_chars(const char* first, const char* last, double& value, chars_format fmt = chars_format::general); 

from_chars_result from_chars(const char* first, const char* last, long double& value, chars_format fmt = chars_format::general);
```

## <a name="get"></a>獲取

依索引位置或依類型從 `pair` 物件取得元素。

```cpp
// get reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
    constexpr tuple_element_t<Index, pair<T1, T2>>&
    get(pair<T1, T2>& Pr) noexcept;

// get reference to element T1 in pair Pr
template <class T1, class T2>
    constexpr T1& get(pair<T1, T2>& Pr) noexcept;

// get reference to element T2 in pair Pr
template <class T2, class T1>
    constexpr T2& get(pair<T1, T2>& Pr) noexcept;

// get const reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
    constexpr const tuple_element_t<Index, pair<T1, T2>>&
    get(const pair<T1, T2>& Pr) noexcept;

// get const reference to element T1 in pair Pr
template <class T1, class T2>
    constexpr const T1& get(const pair<T1, T2>& Pr) noexcept;

// get const reference to element T2 in pair Pr
template <class T2, class T1>
    constexpr const T2& get(const pair<T1, T2>& Pr) noexcept;

// get rvalue reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
    constexpr tuple_element_t<Index, pair<T1, T2>>&&
    get(pair<T1, T2>&& Pr) noexcept;

// get rvalue reference to element T1 in pair Pr
template <class T1, class T2>
    constexpr T1&& get(pair<T1, T2>&& Pr) noexcept;

// get rvalue reference to element T2 in pair Pr
template <class T2, class T1>
    constexpr T2&& get(pair<T1, T2>&& Pr) noexcept;
```

### <a name="parameters"></a>參數

*索引*\
所選擇元素的以零為起始的索引。

*T1*\
第一個配對元素的類型。

*T2*\
第二個配對元素的類型。

*pr*\
要從中選取的配對。

### <a name="remarks"></a>備註

範本函式各自傳回其 `pair` 引數項目的參考。

對於索引多載，如果*index*的值為0，則函式會傳回 `pr.first` 而且如果*index*的值為1，則函式會傳回 `pr.second`。 類型 `RI` 是傳回元素的類型。

對於沒有索引參數的多載，要傳回的元素會由類型引數推算。 如果*pr*包含一個或多個類型 t 的元素，呼叫 `get<T>(Tuple)` 將會產生編譯器錯誤。

### <a name="example"></a>範例

```cpp
#include <utility>
#include <iostream>
using namespace std;
int main()
{

    typedef pair<int, double> MyPair;

    MyPair c0(9, 3.14);

    // get elements by index
    cout << " " << get<0>(c0);
    cout << " " << get<1>(c0) << endl;

    // get elements by type (C++14)
    MyPair c1(1, 0.27);
    cout << " " << get<int>(c1);
    cout << " " << get<double>(c1) << endl;
}
```

```Output
9 3.14
1 0.27
```

## <a name="index_sequence"></a>index_sequence

```cpp
template<size_t... I>
    using index_sequence = integer_sequence<size_t, I...>;
```

## <a name="index_sequence_for"></a>index_sequence_for

```cpp
template<class... T>
    using index_sequence_for = make_index_sequence<sizeof...(T)>;
```

## <a name="make_index_sequence"></a>make_index_sequence

```cpp
template<size_t N>
    using make_index_sequence = make_integer_sequence<size_t, N>;
```

## <a name="make_integer_sequence"></a>make_integer_sequence

```cpp
template<class T, T N>
    using make_integer_sequence = integer_sequence<T, see below >;
```

## <a name="make_pair"></a>make_pair

樣板函式，可用來建構 `pair` 類型物件，其中元件類型是根據做為參數傳遞的資料類型自動選擇。

```cpp
template <class T, class U>
    pair<T, U> make_pair(T& Val1, U& Val2);

template <class T, class U>
    pair<T, U> make_pair(T& Val1, U&& Val2);

template <class T, class U>
    pair<T, U> make_pair(T&& Val1, U& Val2);

template <class T, class U>
    pair<T, U> make_pair(T&& Val1, U&& Val2);
```

### <a name="parameters"></a>參數

*Val1*\
值，初始化 `pair` 的第一個項目。

*Val2*\
值，初始化 `pair` 的第二個項目。

### <a name="return-value"></a>傳回值

所建立的配對物件： `pair`<`T`、`U`> （`Val1`、`Val2`）。

### <a name="remarks"></a>備註

`make_pair` 會將 [reference_wrapper 類別](../standard-library/reference-wrapper-class.md)的型別物件轉換為參考型別，並將衰減陣列和函式轉換為指標。

在傳回的 `pair` 物件，`T` 的判斷方式如下:

- 如果輸入類型 `T` 是 `reference_wrapper<X>`，傳回的類型 `T` 是 `X&`。

- 否則，傳回的類型 `T` 為 `decay<T>::type`。 如果不支援[衰減類別](../standard-library/decay-class.md)，則傳回的型別 `T` 與輸入型別 `T`相同。

傳回的類型 `U` 同樣是根據輸入類型 `U` 判斷。

`make_pair` 的其中一個優點是，編譯器會自動決定所儲存之物件的類型，而不需要明確指定。 當您使用 `make_pair` 時，請勿使用明確樣板引數（例如 `make_pair<int, int>(1, 2)`），因為它是詳細資訊，而且會新增可能造成編譯失敗的複雜右值參考問題。 在這個範例中，正確語法是 `make_pair(1, 2)`。

`make_pair` 協助程式函式也能夠讓您傳遞兩個值給需要成對輸入參數的函式。

### <a name="example"></a>範例

如需如何使用協助程式函式 `make_pair` 宣告並初始化配對的範例，請參閱 [pair 結構](../standard-library/pair-structure.md)。

## <a name="move"></a>進入

無條件地將它的引數轉型為右值參考，因而表示如果其類型已啟用移動，就可以移動它。

```cpp
template <class Type>
    constexpr typename remove_reference<Type>::type&& move(Type&& Arg) noexcept;
```

### <a name="parameters"></a>參數

*類型*\
一種類型，從傳入*Arg*的引數類型推算，連同參考折迭規則。

*Arg*\
要轉型的引數。 雖然*Arg*的類型會指定為右值參考，但 `move` 也會接受左值引數，因為左值參考可以系結至右值參考。

### <a name="return-value"></a>傳回值

`Arg` 做為右值參考，不論它的類型是否為參考類型。

### <a name="remarks"></a>備註

樣板引數*型*別不是要明確指定，而是要從傳入*Arg*的值型別推算。 *類型*的類型會根據參考折迭規則進一步調整。

`move` 不會移動其引數。 相反地，藉由將其引數（可能是左值）無條件地轉型為右值參考，它可讓編譯器在類型已啟用移動的情況下，在*Arg*中傳遞（而不是複製）傳入的值。 如果其類型未啟用移動，則會改為複製它。

如果傳入*Arg*的值為左值（也就是，它有名稱或其位址可以使用），則會在移動發生時失效。 請不要參考其名稱或位址在移動後傳入*Arg*的值。

## <a name="moveif"></a>move_if_noexcept

```cpp
template <class T> constexpr conditional_t< !is_nothrow_move_constructible_v<T> && is_copy_constructible_v<T>, const T&, T&&> move_if_noexcept(T& x) noexcept;
```

## <a name="swap"></a>調換

交換兩個類型或[配對結構](../standard-library/pair-structure.md)物件的元素。

```cpp
template <class T>
    void swap(T& left, T& right) noexcept(see below );
template <class T, size_t N>
    void swap(T (&left)[N], T (&right)[N]) noexcept(is_nothrow_swappable_v<T>);
template <class T, class U>
    void swap(pair<T, U>& left, pair<T, U>& right);
```

### <a name="parameters"></a>參數

*左方*\
`pair`類型或類型的物件。

*right*\
`pair`類型或類型的物件。

### <a name="remarks"></a>備註

`swap` 的其中一個優點是，編譯器會自動決定所儲存之物件的類型，而不需要明確指定。 當您使用 `swap` 時，請勿使用明確樣板引數（例如 `swap<int, int>(1, 2)`），因為它是詳細資訊，而且會新增可能造成編譯失敗的複雜右值參考問題。

## <a name="to_chars"></a>to_chars

```cpp
to_chars_result to_chars(char* first, char* last, see below value, int base = 10);
to_chars_result to_chars(char* first, char* last, float value); 
to_chars_result to_chars(char* first, char* last, double value); 
to_chars_result to_chars(char* first, char* last, long double value);
to_chars_result to_chars(char* first, char* last, float value, chars_format fmt); 
to_chars_result to_chars(char* first, char* last, double value, chars_format fmt); 
to_chars_result to_chars(char* first, char* last, long double value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, float value, chars_format fmt, int precision); 
to_chars_result to_chars(char* first, char* last, double value, chars_format fmt, int precision); 
to_chars_result to_chars(char* first, char* last, long double value, chars_format fmt, int precision);
```

### <a name="remarks"></a>備註

藉由填滿 `[first, last)`的範圍，將值轉換成字元字串，其中 `[first, last)` 必須是有效的範圍。
