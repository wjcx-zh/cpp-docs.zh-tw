---
title: 編譯器錯誤 C3851
ms.date: 09/05/2018
f1_keywords:
- C3851
helpviewer_keywords:
- C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
ms.openlocfilehash: 97d9ef1eeeffa0e5a63d2c8ae2428a3fad0ff238
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165574"
---
# <a name="compiler-error-c3851"></a>編譯器錯誤 C3851

> '*char*'：通用字元名稱不能指定基底字元集中的字元

## <a name="remarks"></a>備註

在編譯為 C++ 的程式碼中，您無法在字串或字元常值之外使用代表基礎來源字元集的通用字元名稱。 如需詳細資訊，請參閱 [Character Sets](../../cpp/character-sets.md)。 在編譯為 C 的程式碼中，除了0x24 （' $ '）、0x40 （'\@'）或0x60 （'\`'）之外，您不能在包含 0x20-0x7f （含）範圍的字元中使用通用字元名稱。

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
