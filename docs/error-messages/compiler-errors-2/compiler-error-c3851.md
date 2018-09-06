---
title: 編譯器錯誤 C3851 |Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3851
dev_langs:
- C++
helpviewer_keywords:
- C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f495a61fd3c157862fe65d82c1ffe5f047d798dd
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43895171"
---
# <a name="compiler-error-c3851"></a>編譯器錯誤 C3851

> '*char*': 通用字元名稱不能指定基礎字元集中的字元

## <a name="remarks"></a>備註

在編譯為 C++ 的程式碼中，您無法在字串或字元常值之外使用代表基礎來源字元集的通用字元名稱。 如需詳細資訊，請參閱 <<c0> [ 字元集](../../cpp/character-sets.md)。 在編譯為 C 程式碼，您無法使用通用字元名稱的字元範圍 0x20 到 0x7f 除外 0x24 （' $'） 中 0x40 ('\@')，或 0x60 ('\`')。

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