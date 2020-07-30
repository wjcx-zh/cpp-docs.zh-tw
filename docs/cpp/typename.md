---
title: typename
ms.date: 11/04/2016
f1_keywords:
- typename_cpp
helpviewer_keywords:
- typename template specifier
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
ms.openlocfilehash: 62e8a2026babbfea3cd1583def05a03b4bc4a229
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223508"
---
# <a name="typename"></a>typename

在範本定義中，會向編譯器提供提示，指出未知的識別碼是一種類型。 在範本參數清單中，是用來指定類型參數。

## <a name="syntax"></a>語法

```
typename identifier;
```

## <a name="remarks"></a>備註

如果範本定義中的名稱是相依于樣板引數的限定名稱，則必須使用此關鍵字;如果限定名稱不相依，這就是選擇性的。 如需詳細資訊，請參閱[範本和名稱解析](../cpp/templates-and-name-resolution.md)。

**`typename`** 可供範本宣告或定義中任何位置的任何類型使用。 除非是做為範本基底類別的樣板引數，否則不允許出現在基底類別清單中。

```cpp
template <class T>
class C1 : typename T::InnerType // Error - typename not allowed.
{};
template <class T>
class C2 : A<typename T::InnerType>  // typename OK.
{};
```

**`typename`** 關鍵字也可以用來取代 **`class`** 範本參數清單中的。 例如，下列語句在語義上是相等的：

```cpp
template<class T1, class T2>...
template<typename T1, typename T2>...
```

## <a name="example"></a>範例

```cpp
// typename.cpp
template<class T> class X
{
   typename T::Y m_y;   // treat Y as a type
};

int main()
{
}
```

## <a name="see-also"></a>另請參閱

[範本](../cpp/templates-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
