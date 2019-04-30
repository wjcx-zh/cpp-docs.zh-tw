---
title: '&lt;string_view&gt; typedefs'
ms.date: 04/19/2019
f1_keywords:
- xstring/std::string_view
- xstring/std::u16string_view
- xstring/std::u32string_view
- xstring/std::wstring_view
ms.openlocfilehash: 16d7ba49facf24dcffb7df444e445d83d92255e0
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346966"
---
# <a name="ltstringviewgt-typedefs"></a>&lt;string_view&gt; typedefs

||||
|-|-|-|
|[string_view](#string_view)|[u16string_view](#u16string_view)|[u32string_view](#u32string_view)|
|[wstring_view](#wstring_view)|

## <a name="string_view"></a> string_view

類型，描述類別樣板的特製化[basic_string_view](../standard-library/basic-string-view-class.md)類型的項目**char**。

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

類型，描述類別樣板的特製化[basic_string_view](../standard-library/basic-string-view-class.md)類型的項目`char16_t`。

```cpp
typedef basic_string_view<char16_t, char_traits<char16_t>> u16string_view;
```

### <a name="remarks"></a>備註

如需 string 建構函式的清單，請參閱 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

## <a name="u32string_view"></a> u32string_view

類型，描述類別樣板的特製化[basic_string_view](../standard-library/basic-string-view-class.md)類型的項目`char32_t`。

```cpp
typedef basic_string_view<char32_t, char_traits<char32_t>> u32string_view;
```

### <a name="remarks"></a>備註

如需 string 建構函式的清單，請參閱 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

## <a name="wstring_view"></a>  wstring_view

類型，描述類別樣板的特製化[basic_string_view](../standard-library/basic-string-view-class.md)類型的項目**wchar_t**。

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
> 大小**wchar_t**是在 Windows 上的兩個位元組，但這不一定適用於所有平台案例。 如果您需要的 string_view 寬字元類型保證會在所有平台上以相同的寬度，使用[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)或是[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)。

## <a name="see-also"></a>另請參閱

[\<string_view>](../standard-library/string-view.md)<br/>
