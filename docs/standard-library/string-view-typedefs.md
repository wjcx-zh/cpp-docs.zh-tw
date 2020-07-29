---
title: '&lt;string_view &gt; typedef'
ms.date: 04/19/2019
f1_keywords:
- xstring/std::string_view
- xstring/std::u16string_view
- xstring/std::u32string_view
- xstring/std::wstring_view
ms.openlocfilehash: 6aadd4ad3ff08a0b020fd8e683e60063fe516c63
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215591"
---
# <a name="ltstring_viewgt-typedefs"></a>&lt;string_view &gt; typedef

||||
|-|-|-|
|[string_view](#string_view)|[u16string_view](#u16string_view)|[u32string_view](#u32string_view)|
|[wstring_view](#wstring_view)|

## <a name="string_view"></a><a name="string_view"></a>string_view

一種類型，描述類別樣板的特製化， [basic_string_view](../standard-library/basic-string-view-class.md)具有類型的元素 **`char`** 。

```cpp
typedef basic_string_view<char, char_traits<char>> string_view;
```

### <a name="remarks"></a>備註

以下宣告是相同的：

```cpp
string_view str("Hello");

basic_string_view<char> str("Hello");
```

如需 string 建構函式的清單，請參閱 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

## <a name="u16string_view"></a><a name="u16string_view"></a>u16string_view

一種類型，描述類別樣板的特製化， [basic_string_view](../standard-library/basic-string-view-class.md)具有類型的元素 **`char16_t`** 。

```cpp
typedef basic_string_view<char16_t, char_traits<char16_t>> u16string_view;
```

### <a name="remarks"></a>備註

如需 string 建構函式的清單，請參閱 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

## <a name="u32string_view"></a><a name="u32string_view"></a>u32string_view

一種類型，描述類別樣板的特製化， [basic_string_view](../standard-library/basic-string-view-class.md)具有類型的元素 **`char32_t`** 。

```cpp
typedef basic_string_view<char32_t, char_traits<char32_t>> u32string_view;
```

### <a name="remarks"></a>備註

如需 string 建構函式的清單，請參閱 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

## <a name="wstring_view"></a><a name="wstring_view"></a>wstring_view

一種類型，描述類別樣板的特製化， [basic_string_view](../standard-library/basic-string-view-class.md)具有類型的元素 **`wchar_t`** 。

```cpp
typedef basic_string_view<wchar_t, char_traits<wchar_t>> wstring_view;
```

### <a name="remarks"></a>備註

以下宣告是相同的：

```cpp
wstring_view wstr(L"Hello");

basic_string_view<wchar_t> wstr(L"Hello");
```

如需 string 建構函式的清單，請參閱 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

> [!NOTE]
> 的大小 **`wchar_t`** 是 Windows 上的兩個位元組，但是並非所有平臺都有這種情況。 如果您需要 string_view 寬字元類型，且其寬度保證在所有平臺上都維持不變，請使用[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)或[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)。

## <a name="see-also"></a>另請參閱

[\<string_view>](../standard-library/string-view.md)
