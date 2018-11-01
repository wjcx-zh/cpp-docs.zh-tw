---
title: typename
ms.date: 11/04/2016
f1_keywords:
- typename_cpp
helpviewer_keywords:
- typename template specifier
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
ms.openlocfilehash: 7dbe4381465036bdd102b3be753a18451886a3d8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665851"
---
# <a name="typename"></a>typename

在樣板定義中提供提示給編譯器未知的識別項是型別。 在範本參數清單中，用來指定的型別參數上。

## <a name="syntax"></a>語法

```
typename identifier;
```

## <a name="remarks"></a>備註

如果範本定義中的名稱是限定的名稱，取決於樣板引數，則必須使用這個關鍵字它是選擇性的如果限定的名稱無關。 如需詳細資訊，請參閱 <<c0> [ 樣板和名稱解析](../cpp/templates-and-name-resolution.md)。

**typename**可由樣板宣告或定義中的任何類型。 除非是做為範本基底類別的樣板引數，否則不允許出現在基底類別清單中。

```cpp
template <class T>
class C1 : typename T::InnerType // Error - typename not allowed.
{};
template <class T>
class C2 : A<typename T::InnerType>  // typename OK.
{};
```

**Typename**關鍵字也用於取代**類別**在樣板參數清單。 例如，下列陳述式是語意上相等的：

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