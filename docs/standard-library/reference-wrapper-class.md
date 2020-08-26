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
ms.openlocfilehash: 623e1480bdec85120e504c8dc71b28d017c8872a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845064"
---
# <a name="reference_wrapper-class"></a>reference_wrapper 類別

包裝一個參考。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
class reference_wrapper
{
    typedef Ty type;

    reference_wrapper(Ty&) noexcept;
    operator Ty&() const noexcept;
    Ty& get() const noexcept;

    template <class... Types>
    auto operator()(Types&&... args) const ->
        decltype(std::invoke(get(), std::forward<Types>(args)...));
};
```

## <a name="remarks"></a>備註

`reference_wrapper<Ty>` 是 `Ty` 類型的物件或函式之參考周圍的可複製建構且可複製指派的包裝函式，並會保存指向該類型之物件的指標。 `reference_wrapper` 可用來將參考儲存於標準容器中，並以傳址方式將物件傳遞到 `std::bind`。

`Ty` 類型必須是物件類型或函式類型，否則靜態判斷提示會在編譯期間失敗。

Helper 函式 [std::ref](functional-functions.md#ref) 和 [std::cref](functional-functions.md#cref) 可用來建立 `reference_wrapper` 物件。

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|名稱|描述|
|-|-|
|[reference_wrapper](#reference_wrapper)|建構 `reference_wrapper`。|

### <a name="typedefs"></a>Typedefs

|名稱|描述|
|-|-|
|[result_type](#result_type)|包裝之參考的弱式結果類型。|
|[type](#type)|包裝的參考類型。|

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[get](#get)|取得包裝的參考。|

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[運算子 Ty&amp;](#op_ty_amp)|取得包裝的參考指標。|
|[運算子 ( # B1 ](#op_call)|呼叫包裝的參考。|

## <a name="get"></a><a name="get"></a> 獲取

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

## <a name="operator-tyamp"></a><a name="op_ty_amp"></a> 運算子 Ty&amp;

取得包裝的參考。

```cpp
operator Ty&() const noexcept;
```

### <a name="remarks"></a>備註

成員運算子會傳回 `*ptr`。

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

## <a name="operator"></a><a name="op_call"></a> 運算子 ( # A1

呼叫包裝的參考。

```cpp
template <class... Types>
auto operator()(Types&&... args);
```

### <a name="parameters"></a>參數

*類型*\
引數清單類型。

*參數*\
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

## <a name="reference_wrapper"></a><a name="reference_wrapper"></a> reference_wrapper

建構 `reference_wrapper`。

```cpp
reference_wrapper(Ty& val) noexcept;
```

### <a name="parameters"></a>參數

*泰*\
要包裝的類型。

*瓦爾*\
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

## <a name="result_type"></a><a name="result_type"></a> result_type

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

## <a name="type"></a><a name="type"></a> 類型

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
