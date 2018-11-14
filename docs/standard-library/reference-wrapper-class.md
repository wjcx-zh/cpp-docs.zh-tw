---
title: reference_wrapper 類別
ms.date: 11/04/2016
f1_keywords:
- functional/std::reference_wrapper
- type_traits/std::reference_wrapper
- xrefwrap/std::reference_wrapper
- type_traits/std::reference_wrapper::get
- type_traits/std::reference_wrapper::operator()
- functional/std::reference_wrapper::result_type
- functional/std::reference_wrapper::type
- functional/std::reference_wrapper::get
- functional/std::reference_wrapper::operator()
helpviewer_keywords:
- std::reference_wrapper [C++]
- std::reference_wrapper [C++]
- std::reference_wrapper [C++], result_type
- std::reference_wrapper [C++], type
- std::reference_wrapper [C++], get
ms.assetid: 90b8ed62-e6f1-44ed-acc7-9619bd58865a
ms.openlocfilehash: baf38dd637e31f6fabdf869a242f8f18e2812717
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51525232"
---
# <a name="referencewrapper-class"></a>reference_wrapper 類別

包裝一個參考。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
class reference_wrapper
{
public:
    typedef Ty type;

    reference_wrapper(Ty&) noexcept;
    operator Ty&() const noexcept;
    Ty& get() const noexcept;

    template <class... Types>
    auto operator()(Types&&... args) const ->
        decltype(std::invoke(get(), std::forward<Types>(args)...));

private:
    Ty *ptr; // exposition only
};
```

## <a name="remarks"></a>備註

`reference_wrapper<Ty>` 是 `Ty` 類型的物件或函式之參考周圍的可複製建構且可複製指派的包裝函式，並會保存指向該類型之物件的指標。 `reference_wrapper` 可用來將參考儲存於標準容器中，並以傳址方式將物件傳遞到 `std::bind`。

`Ty` 類型必須是物件類型或函式類型，否則靜態判斷提示會在編譯期間失敗。

Helper 函式 [std::ref](functional-functions.md#ref) 和 [std::cref](functional-functions.md#cref) 可用來建立 `reference_wrapper` 物件。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[reference_wrapper](#reference_wrapper)|建構 `reference_wrapper`。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[result_type](#result_type)|包裝之參考的弱式結果類型。|
|[type](#type)|包裝的參考類型。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[get](#get)|取得包裝的參考。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[reference_wrapper::operator Ty&amp;](#op_ty_amp)|取得包裝的參考指標。|
|[reference_wrapper::operator()](#op_call)|呼叫包裝的參考。|

## <a name="requirements"></a>需求

**標頭：**\<functional>

**命名空間：** std

## <a name="get"></a>  reference_wrapper::get

取得包裝的參考。

```cpp
Ty& get() const noexcept;
```

### <a name="remarks"></a>備註

成員函式會傳回包裝的參考。

### <a name="example"></a>範例

```cpp
// std__functional__reference_wrapper_get.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int main() {
    int i = 1;
    std::reference_wrapper<int> rwi(i);

    std::cout << "i = " << i << std::endl;
    std::cout << "rwi = " << rwi << std::endl;
    rwi.get() = -1;
    std::cout << "i = " << i << std::endl;

    return (0);
}
```

```Output
i = 1
rwi = 1
i = -1
```

## <a name="op_ty_amp"></a>  reference_wrapper::operator Ty&amp;

取得包裝的參考。

```cpp
operator Ty&() const noexcept;
```

### <a name="remarks"></a>備註

此成員運算子會傳回 `*ptr`。

### <a name="example"></a>範例

```cpp
// std__functional__reference_wrapper_operator_cast.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int main() {
    int i = 1;
    std::reference_wrapper<int> rwi(i);

    std::cout << "i = " << i << std::endl;
    std::cout << "(int)rwi = " << (int)rwi << std::endl;

    return (0);
}
```

```Output
i = 1
(int)rwi = 1
```

## <a name="op_call"></a>  reference_wrapper::operator()

呼叫包裝的參考。

```cpp
template <class... Types>
auto operator()(Types&&... args);
```

### <a name="parameters"></a>參數

*型別*<br/>
引數清單類型。

*引數*<br/>
引數清單。

### <a name="remarks"></a>備註

範本成員 `operator()` 會傳回 `std::invoke(get(), std::forward<Types>(args)...)`。

### <a name="example"></a>範例

```cpp
// std__functional__reference_wrapper_operator_call.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val) {
    return (-val);
}

int main() {
    std::reference_wrapper<int (int)> rwi(neg);

    std::cout << "rwi(3) = " << rwi(3) << std::endl;

    return (0);
}
```

```Output
rwi(3) = -3
```

## <a name="reference_wrapper"></a>  reference_wrapper::reference_wrapper

建構 `reference_wrapper`。

```cpp
reference_wrapper(Ty& val) noexcept;
```

### <a name="parameters"></a>參數

*Ty*<br/>
要包裝的類型。

*val*<br/>
要包裝的值。

### <a name="remarks"></a>備註

建構函式會將儲存的值 `ptr` 設為 `&val`。

### <a name="example"></a>範例

```cpp
// std__functional__reference_wrapper_reference_wrapper.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val) {
    return (-val);
}

int main() {
    int i = 1;
    std::reference_wrapper<int> rwi(i);

    std::cout << "i = " << i << std::endl;
    std::cout << "rwi = " << rwi << std::endl;
    rwi.get() = -1;
    std::cout << "i = " << i << std::endl;

    return (0);
}
```

```Output
i = 1
rwi = 1
i = -1
```

## <a name="result_type"></a>  reference_wrapper::result_type

包裝之參考的弱式結果類型。

```cpp
typedef R result_type;
```

### <a name="remarks"></a>備註

`result_type` Typedef 與已包裝函式的弱式結果類型同義。 這個 typedef 僅適用於函式類型。

### <a name="example"></a>範例

```cpp
// std__functional__reference_wrapper_result_type.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val) {
    return (-val);
}

int main() {
    typedef std::reference_wrapper<int (int)> Mywrapper;
    Mywrapper rwi(neg);
    Mywrapper::result_type val = rwi(3);

    std::cout << "val = " << val << std::endl;

    return (0);
}
```

```Output
val = -3
```

## <a name="type"></a>  reference_wrapper::type

包裝的參考類型。

```cpp
typedef Ty type;
```

### <a name="remarks"></a>備註

typedef 是範本引數 `Ty`的同義字。

### <a name="example"></a>範例

```cpp
// std__functional__reference_wrapper_type.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val) {
    return (-val);
}

int main() {
    int i = 1;
    typedef std::reference_wrapper<int> Mywrapper;
    Mywrapper rwi(i);
    Mywrapper::type val = rwi.get();

    std::cout << "i = " << i << std::endl;
    std::cout << "rwi = " << val << std::endl;

    return (0);
}
```

```Output
i = 1
rwi = 1
```

## <a name="see-also"></a>另請參閱

[cref](../standard-library/functional-functions.md#cref)<br/>
[ref](../standard-library/functional-functions.md#ref)<br/>
