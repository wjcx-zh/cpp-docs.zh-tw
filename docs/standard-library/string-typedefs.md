---
title: '&lt;string&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- string/std::string
- string/std::u16string
- string/std::u32string
- string/std::wstring
ms.assetid: fdca01e9-f2f1-4b59-abda-0093d760b3cc
ms.openlocfilehash: 8e662e4c13012f31014817489b61ee3ed6bc36e0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87202294"
---
# <a name="ltstringgt-typedefs"></a>&lt;string&gt; typedef

||||
|-|-|-|
|[string](#string)|[u16string](#u16string)|[u32string](#u32string)|
|[wstring](#wstring)|

## <a name="string"></a><a name="string"></a> 字串

一種類型，描述類別樣板的特製化， [basic_string](../standard-library/basic-string-class.md)具有類型的元素 **`char`** 。

其他特製化 `basic_string` 的 typedef 包含 [wstring](../standard-library/string-typedefs.md#wstring)、[u16string](../standard-library/string-typedefs.md#u16string) 及 [u32string](../standard-library/string-typedefs.md#u32string)。

```cpp
typedef basic_string<char, char_traits<char>, allocator<char>> string;
```

### <a name="remarks"></a>備註

以下宣告是相同的：

```cpp
string str("");

basic_string<char> str("");
```

如需 string 建構函式的清單，請參閱 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

## <a name="u16string"></a><a name="u16string"></a>u16string

一種類型，描述類別樣板的特製化， [basic_string](../standard-library/basic-string-class.md)具有類型的元素 **`char16_t`** 。

其他特製化 `basic_string` 的 typedef 包含 [wstring](../standard-library/string-typedefs.md#wstring)、[string](../standard-library/string-typedefs.md#string) 及 [u32string](../standard-library/string-typedefs.md#u32string)。

```cpp
typedef basic_string<char16_t, char_traits<char16_t>, allocator<char16_t>> u16string;
```

### <a name="remarks"></a>備註

如需 string 建構函式的清單，請參閱 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

## <a name="u32string"></a><a name="u32string"></a>u32string

一種類型，描述類別樣板的特製化， [basic_string](../standard-library/basic-string-class.md)具有類型的元素 **`char32_t`** 。

其他特製化 `basic_string` 的 typedef 包含 [string](../standard-library/string-typedefs.md#string)、[u16string](../standard-library/string-typedefs.md#u16string) 及 [wstring](../standard-library/string-typedefs.md#wstring)。

```cpp
typedef basic_string<char32_t, char_traits<char32_t>, allocator<char32_t>> u32string;
```

### <a name="remarks"></a>備註

如需 string 建構函式的清單，請參閱 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

## <a name="wstring"></a><a name="wstring"></a>wstring

一種類型，描述類別樣板的特製化， [basic_string](../standard-library/basic-string-class.md)具有類型的元素 **`wchar_t`** 。

其他特製化 `basic_string` 的 typedef 包含 [string](../standard-library/string-typedefs.md#string)、[u16string](../standard-library/string-typedefs.md#u16string) 及 [u32string](../standard-library/string-typedefs.md#u32string)。

```cpp
typedef basic_string<wchar_t, char_traits<wchar_t>, allocator<wchar_t>> wstring;
```

### <a name="remarks"></a>備註

以下宣告是相同的：

```cpp
wstring wstr(L"");

basic_string<wchar_t> wstr(L"");
```

如需 string 建構函式的清單，請參閱 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

> [!NOTE]
> 的大小 **`wchar_t`** 是實作為定義的。 如果您的程式碼相依于 **`wchar_t`** 特定大小，請檢查平臺的執行（例如，使用 `sizeof(wchar_t)` ）。 如果您需要的字串字元類型保證會在所有平台上具有相同寬度，請使用 [string](../standard-library/string-typedefs.md#string)、[u16string](../standard-library/string-typedefs.md#u16string) 或 [u32string](../standard-library/string-typedefs.md#u32string)。

## <a name="see-also"></a>另請參閱

[\<string>](../standard-library/string.md)
