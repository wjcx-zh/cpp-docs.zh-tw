---
title: 編譯器錯誤 C3851
ms.date: 09/05/2018
f1_keywords:
- C3851
helpviewer_keywords:
- C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
ms.openlocfilehash: 52c4f3a393ffaf2b61a65c8e2e0dcc8efac08288
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380938"
---
# <a name="compiler-error-c3851"></a>編譯器錯誤 C3851

> '*char*': 通用字元名稱不能指定基礎字元集中的字元

## <a name="remarks"></a>備註

在編譯為 C++ 的程式碼中，您無法在字串或字元常值之外使用代表基礎來源字元集的通用字元名稱。 如需詳細資訊，請參閱 [Character Sets](../../cpp/character-sets.md)。 在編譯為 C 程式碼，您無法使用通用字元名稱的字元範圍 0x20 到 0x7f 除外 0x24 （' $'） 中 0x40 ('\@')，或 0x60 ('\`')。

## <a name="example"></a>範例

下列範例會產生 C3851，並顯示如何修正此問題：

```cpp
// C3851.cpp
int main()
{
   int test1_\u0041 = 0;   // C3851, \u0041 = 'A' in basic character set
   int test2_A = 0;        // OK
}
```