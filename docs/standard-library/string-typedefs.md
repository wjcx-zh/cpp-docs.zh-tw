---
title: '&lt;string&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- string/std::string
- string/std::u16string
- string/std::u32string
- string/std::wstring
ms.assetid: fdca01e9-f2f1-4b59-abda-0093d760b3cc
ms.openlocfilehash: 534c51e8a627ca893ea42e023f12d8bc62d6fb5c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456273"
---
# <a name="ltstringgt-typedefs"></a>&lt;string&gt; typedef

||||
|-|-|-|
|[string](#string)|[u16string](#u16string)|[u32string](#u32string)|
|[wstring](#wstring)|

## <a name="string"></a>  string

類型，描述範本類別的特製化[basic_string](../standard-library/basic-string-class.md)類型的項目**char**。

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

## <a name="u16string"></a>  u16string

類型，描述使用 `char16_t` 類型的項目特製化樣板類別 [basic_string](../standard-library/basic-string-class.md)。

其他特製化 `basic_string` 的 typedef 包含 [wstring](../standard-library/string-typedefs.md#wstring)、[string](../standard-library/string-typedefs.md#string) 及 [u32string](../standard-library/string-typedefs.md#u32string)。

```cpp
typedef basic_string<char16_t, char_traits<char16_t>, allocator<char16_t>> u16string;
```

### <a name="remarks"></a>備註

如需 string 建構函式的清單，請參閱 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

## <a name="u32string"></a>  u32string

類型，描述使用 `char32_t` 類型的項目特製化樣板類別 [basic_string](../standard-library/basic-string-class.md)。

其他特製化 `basic_string` 的 typedef 包含 [string](../standard-library/string-typedefs.md#string)、[u16string](../standard-library/string-typedefs.md#u16string) 及 [wstring](../standard-library/string-typedefs.md#wstring)。

```cpp
typedef basic_string<char32_t, char_traits<char32_t>, allocator<char32_t>> u32string;
```

### <a name="remarks"></a>備註

如需 string 建構函式的清單，請參閱 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

## <a name="wstring"></a>  wstring

類型，描述範本類別的特製化[basic_string](../standard-library/basic-string-class.md)類型的項目**wchar_t**。

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
> 大小**wchar_t**是由實作定義。 如果您的程式碼相依於**wchar_t**若要為特定的大小，請檢查您的平台實作 (例如，使用`sizeof(wchar_t)`)。 如果您需要的字串字元類型保證會在所有平台上具有相同寬度，請使用 [string](../standard-library/string-typedefs.md#string)、[u16string](../standard-library/string-typedefs.md#u16string) 或 [u32string](../standard-library/string-typedefs.md#u32string)。

## <a name="see-also"></a>另請參閱

[\<string>](../standard-library/string.md)<br/>
