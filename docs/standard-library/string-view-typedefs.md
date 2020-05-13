---
title: '&lt;string_view&gt;型態定義'
ms.date: 04/19/2019
f1_keywords:
- xstring/std::string_view
- xstring/std::u16string_view
- xstring/std::u32string_view
- xstring/std::wstring_view
ms.openlocfilehash: 0ec278484b7c1c9887771f6cbe7e5d0b05205dd7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376668"
---
# <a name="ltstring_viewgt-typedefs"></a>&lt;string_view&gt;型態定義

||||
|-|-|-|
|[string_view](#string_view)|[u16string_view](#u16string_view)|[u32string_view](#u32string_view)|
|[wstring_view](#wstring_view)|

## <a name="string_view"></a><a name="string_view"></a>string_view

描述類範本的專門化[basic_string_view](../standard-library/basic-string-view-class.md)類型**為 char。**

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

描述[類範本的](../standard-library/basic-string-view-class.md)專門化basic_string_view的類型,`char16_t`具有類型的元素。

```cpp
typedef basic_string_view<char16_t, char_traits<char16_t>> u16string_view;
```

### <a name="remarks"></a>備註

如需 string 建構函式的清單，請參閱 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

## <a name="u32string_view"></a><a name="u32string_view"></a>u32string_view

描述[類範本的](../standard-library/basic-string-view-class.md)專門化basic_string_view的類型,`char32_t`具有類型的元素。

```cpp
typedef basic_string_view<char32_t, char_traits<char32_t>> u32string_view;
```

### <a name="remarks"></a>備註

如需 string 建構函式的清單，請參閱 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

## <a name="wstring_view"></a><a name="wstring_view"></a>wstring_view

描述類範本的專門化的類型[basic_string_view,](../standard-library/basic-string-view-class.md)該類型**wchar_t**的元素。

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
> **wchar_t**的大小在 Windows 上為兩個字節,但並非所有平臺都如此。 如果需要string_view寬字元類型,其寬度保證在所有平臺上保持不變,請使用[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)或[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)。

## <a name="see-also"></a>另請參閱

[\<string_view>](../standard-library/string-view.md)
