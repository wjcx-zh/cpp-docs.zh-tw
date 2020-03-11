---
title: '&lt;unordered_set&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- unordered_set/std::swap (set)
- unordered_set/std::swap (unordered_multiset)
ms.assetid: 66b35671-4023-4411-ad50-83786580d8ee
ms.openlocfilehash: 6b6e764acc9fa3410a44a4a11760933328365852
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890725"
---
# <a name="ltunordered_setgt-functions"></a>&lt;unordered_set&gt; 函式

## <a name="swap"></a>交換（unordered_set）

交換兩個容器的內容。

```cpp
template <class Key, class Hash, class Pred, class Alloc>
void swap(
   unordered_set <Key, Hash, Pred, Alloc>& left,
   unordered_set <Key, Hash, Pred, Alloc>& right);
```

### <a name="parameters"></a>參數

*金鑰*\
索引鍵類型。

*雜湊*\
雜湊函式物件類型。

*Pred*\
相等比較函式物件類型。

配置\
配置器類別。

*左方*\
要交換的第一個容器。

*right*\
要交換的第二個容器。

### <a name="remarks"></a>備註

範本函式執行 `left.`[unordered_set::swap](../standard-library/unordered-set-class.md#swap)`(right)`。

### <a name="example"></a>範例

```cpp
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
Myset c1;

c1.insert('a');
c1.insert('b');
c1.insert('c');

// display contents " [c] [b] [a]"
for (Myset::const_iterator it = c1.begin();
it != c1.end(); ++it)
std::cout << " [" << *it << "]";
std::cout << std::endl;

Myset c2;

c2.insert('d');
c2.insert('e');
c2.insert('f');

c1.swap(c2);

// display contents " [f] [e] [d]"
for (Myset::const_iterator it = c1.begin();
it != c1.end(); ++it)
std::cout << " [" << *it << "]";
std::cout << std::endl;

swap(c1, c2);

// display contents " [c] [b] [a]"
for (Myset::const_iterator it = c1.begin();
it != c1.end(); ++it)
std::cout << " [" << *it << "]";
std::cout << std::endl;

return (0);
}
```

```Output
[c] [b] [a]
[f] [e] [d]
[c] [b] [a]
```

## <a name="swap_unordered_multiset"></a>交換（unordered_multiset）

交換兩個容器的內容。

```cpp
template <class Key, class Hash, class Pred, class Alloc>
void swap(
   unordered_multiset <Key, Hash, Pred, Alloc>& left,
   unordered_multiset <Key, Hash, Pred, Alloc>& right);
```

### <a name="parameters"></a>參數

*金鑰*\
索引鍵類型。

*雜湊*\
雜湊函式物件類型。

*Pred*\
相等比較函式物件類型。

配置\
配置器類別。

*左方*\
要交換的第一個容器。

*right*\
要交換的第二個容器。

### <a name="remarks"></a>備註

範本函式執行 `left.`[unordered_multiset::swap](../standard-library/unordered-multiset-class.md#swap)`(right)`。

### <a name="example"></a>範例

```cpp
// std__unordered_set__u_ms_swap.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    Myset c2;

    c2.insert('d');
    c2.insert('e');
    c2.insert('f');

    c1.swap(c2);

    // display contents " [f] [e] [d]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    swap(c1, c2);

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
[f] [e] [d]
[c] [b] [a]
```
