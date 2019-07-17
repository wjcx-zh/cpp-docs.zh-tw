---
title: '&lt;filesystem&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- FILESYSTEM/std::experimental::filesystem::operator==
- FILESYSTEM/std::experimental::filesystem::operator!=
- FILESYSTEM/std::experimental::filesystem::operator<
- FILESYSTEM/std::experimental::filesystem::operator<=
- FILESYSTEM/std::experimental::filesystem::operator>
- FILESYSTEM/std::experimental::filesystem::operator>=
- FILESYSTEM/std::experimental::filesystem::operator/
- FILESYSTEM/std::experimental::filesystem::operator<<
- FILESYSTEM/std::experimental::filesystem::operator>>
ms.assetid: 102c4833-aa3b-41a8-8998-f5003c546bfd
ms.openlocfilehash: 819c91e707e50a190aa58eda62f8e07f3451b033
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240720"
---
# <a name="ltfilesystemgt-operators"></a>&lt;filesystem&gt; 運算子

這些運算子會將兩個路徑的語彙比較當做字串來執行。 使用`equivalent`函式來判斷兩個路徑 （例如相對路徑和絕對路徑） 是否參考相同的檔案或目錄在磁碟上的。

如需詳細資訊，請參閱[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)。

## <a name="operator"></a>operator==

```cpp
bool operator==(const path& left, const path& right) noexcept;
```

此函式會傳回 left.native() == right.native()。

## <a name="operator"></a>operator!=

```cpp
bool operator!=(const path& left, const path& right) noexcept;
```

此函式會傳回 !(left == right)。

## <a name="operator"></a>operator<

```cpp
bool operator<(const path& left, const path& right) noexcept;
```

此函式會傳回 left.native() < right.native()。

## <a name="operator"></a>operator<=

```cpp
bool operator<=(const path& left, const path& right) noexcept;
```

此函式會傳回 !(right \< left)。

## <a name="operator"></a>operator>

```cpp
bool operator>(const path& left, const path& right) noexcept;
```

此函式會傳回 \< left。

## <a name="operator"></a>operator>=

```cpp
bool operator>=(const path& left, const path& right) noexcept;
```

此函式會傳回 !(left < right)。

## <a name="operator"></a>operator/

```cpp
path operator/(const path& left, const path& right);
```

此函式會執行：

```cpp
basic_string<Elem, Traits> str;
path ans = left;
return (ans /= right);
```

## <a name="operator"></a>operator<<

```cpp
template <class Elem, class Traits>
basic_ostream<Elem, Traits>& operator<<(basic_ostream<Elem, Traits>& os, const path& pval);
```

此函式會傳回 os << pval.string\<Elem, Traits>()。

## <a name="operator"></a>operator>>

```cpp
template <class Elem, class Traits>
basic_istream<Elem, Traits>& operator<<(basic_istream<Elem, Traits>& is, const path& pval);
```

此函式會執行：

```cpp
basic_string<Elem, Traits> str;
is>> str;
pval = str;
return (is);
```
