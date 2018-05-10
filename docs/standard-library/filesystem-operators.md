---
title: '&lt;filesystem&gt; 運算子 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 102c4833-aa3b-41a8-8998-f5003c546bfd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 546e601afeb05e0347dba8bf792611f20068c69b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="ltfilesystemgt-operators"></a>&lt;filesystem&gt; 運算子

這些運算子會將兩個路徑的語彙比較當做字串來執行。 使用 **equivalent** 函式可判斷兩個路徑 (例如相對路徑和絕對路徑) 是否參考磁碟上的相同檔案或目錄。

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

## <a name="see-also"></a>另請參閱

[path 類別 （c + + 標準程式庫）](../standard-library/path-class.md)<br/>
[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
