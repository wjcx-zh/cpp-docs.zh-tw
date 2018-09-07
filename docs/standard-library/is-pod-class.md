---
title: is_pod 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_pod
dev_langs:
- C++
helpviewer_keywords:
- is_pod class
- is_pod
ms.assetid: d73ebdee-746b-4082-9fa4-2db71432eb0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 652937aba7b1c5626b617cec4e80761a22b55066
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44109819"
---
# <a name="ispod-class"></a>is_pod 類別

測試類型是否為 POD。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_pod;
```

### <a name="parameters"></a>參數

*T*<br/>
要查詢的類型。

## <a name="remarks"></a>備註

`is_pod<T>::value` 已**真**如果型別*T*是一般舊資料 (POD)。 否則，它會**false**。

算術類型、列舉類型、指標類型和成員類型的指標是 POD。

POD 類型的 cv-qualified 版本本身是 POD 類型。

POD 的陣列本身是 POD。

結構或等位 (其所有的非靜態資料成員皆為 POD) 本身是 POD，前提是：

- 沒有使用者宣告的建構函式。

- 沒有私人或受保護的非靜態資料成員。

- 沒有基底類別。

- 沒有虛擬函式。

- 沒有參考類型的非靜態資料成員。

- 沒有使用者定義的複製指派運算子。

- 沒有使用者定義的解構函式。

因此，您可以用遞迴方式建置包含 POD 結構和陣列的 POD 結構和陣列。

## <a name="example"></a>範例

```cpp
// std__type_traits__is_pod.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial {
    int val;
};

struct throws {
    throws() {}  // User-declared ctor, so not POD

    int val;
};

int main() {
    std::cout << "is_pod<trivial> == " << std::boolalpha
        << std::is_pod<trivial>::value << std::endl;
    std::cout << "is_pod<int> == " << std::boolalpha
        << std::is_pod<int>::value << std::endl;
    std::cout << "is_pod<throws> == " << std::boolalpha
        << std::is_pod<throws>::value << std::endl;

    return (0);
}
```

```Output
is_pod<trivial> == true
is_pod<int> == true
is_pod<throws> == false
```

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
