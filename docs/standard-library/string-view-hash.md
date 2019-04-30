---
title: 雜湊&lt;string_view&gt;特製化
ms.date: 04/19/2019
f1_keywords:
- xstring/basic_string_view::hash
helpviewer_keywords:
- std::basic_string_view::hash
ms.openlocfilehash: 60b6fdecc371ee950532dee3f69cc8dd07b8b5eb
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346956"
---
# <a name="hashltstringviewgt-specialization"></a>雜湊&lt;string_view&gt;特製化

樣板特製化會產生給定 string_view 的雜湊值。

```cpp
template <class CharType, class Traits>
struct hash<basic_string_view<CharType, Traits>>
{
    typedef basic_string_view<CharType, Traits> argument_type;
    typedef size_t result_type;

    size_t operator()(const basic_string_view<CharType, Traits>) const
        noexcept;
};
```
### <a name="remarks"></a>備註

String_view 的雜湊值等於基礎字串物件的雜湊。

### <a name="example"></a>範例

```cpp
//compile with: /std:c++17
#include <string>
#include <string_view>
#include <iostream>

using namespace std;

int main()
{
    string_view sv{ "Hello world" };
    string s{ "Hello world" };
    cout << boolalpha << (hash<string_view>{}(sv)
        == hash<string>{}(s)); // true
}
```