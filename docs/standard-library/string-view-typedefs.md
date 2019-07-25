---
title: '&lt;string_view&gt; typedef'
ms.date: 04/19/2019
f1_keywords:
- xstring/std::string_view
- xstring/std::u16string_view
- xstring/std::u32string_view
- xstring/std::wstring_view
ms.openlocfilehash: c3367afe1353ac70abb74a59658a255614ac8470
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459175"
---
# <a name="ltstringviewgt-typedefs"></a>&lt;string_view&gt; typedef

||||
|-|-|-|
|[string_view](#string_view)|[u16string_view](#u16string_view)|[u32string_view](#u32string_view)|
|[wstring_view](#wstring_view)|

## <a name="string_view"></a> string_view

一種類型, 描述以**char**類型的元素[basic_string_view](../standard-library/basic-string-view-class.md)之類別樣板的特製化。

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

## <a name="u16string_view"></a> u16string_view

一種類型, 描述具有類型`char16_t`之元素的類別樣板[basic_string_view](../standard-library/basic-string-view-class.md)的特製化。

```cpp
typedef basic_string_view<char16_t, char_traits<char16_t>> u16string_view;
```

### <a name="remarks"></a>備註

如需 string 建構函式的清單，請參閱 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

## <a name="u32string_view"></a> u32string_view

一種類型, 描述具有類型`char32_t`之元素的類別樣板[basic_string_view](../standard-library/basic-string-view-class.md)的特製化。

```cpp
typedef basic_string_view<char32_t, char_traits<char32_t>> u32string_view;
```

### <a name="remarks"></a>備註

如需 string 建構函式的清單，請參閱 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

## <a name="wstring_view"></a>  wstring_view

一種類型, 描述以**wchar_t**類型的元素[basic_string_view](../standard-library/basic-string-view-class.md)的類別樣板特製化。

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
> **Wchar_t**的大小是 Windows 上的兩個位元組, 但並非所有平臺的情況。 如果您需要 string_view 寬字元類型, 且其寬度保證在所有平臺上都維持不變, 請使用[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)或[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)。

## <a name="see-also"></a>另請參閱

[\<string_view>](../standard-library/string-view.md)
