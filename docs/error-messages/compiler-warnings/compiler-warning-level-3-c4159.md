---
title: 編譯器警告（層級3） C4159
ms.date: 11/04/2016
f1_keywords:
- C4159
helpviewer_keywords:
- C4159
ms.assetid: e2cf964e-f4b8-4b2c-9569-1abb94307232
ms.openlocfilehash: 20d6010cb83107946c00f2f7b00cda771b2e70b9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199013"
---
# <a name="compiler-warning-level-3-c4159"></a>編譯器警告（層級3） C4159

> #<a name="pragma-pragmapop--has-popped-previously-pushed-identifier-identifier"></a>pragma pragma （pop,...）：已彈出先前推送的識別碼 '*identifier*'

## <a name="remarks"></a>備註

您的原始程式碼包含含有 pragma 識別碼的**推送**指示，後面接著沒有識別碼的**pop**指令。 因此，*識別碼*會隨即推出，而後續的*識別碼*使用可能會導致非預期的行為。

## <a name="example"></a>範例

若要避免這個警告，請在**pop**指示中提供識別碼。 例如：

```cpp
// C4159.cpp
// compile with: /W3
#pragma pack(push, f)
#pragma pack(pop)   // C4159

// using the identifier resolves the warning
// #pragma pack(pop, f)

int main()
{
}
```
