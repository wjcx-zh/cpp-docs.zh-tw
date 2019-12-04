---
title: 編譯器錯誤 C3846
ms.date: 11/04/2016
f1_keywords:
- C3846
helpviewer_keywords:
- C3846
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
ms.openlocfilehash: a4c51ccfc724cf8309044812b287677f0f1a2ff0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754897"
---
# <a name="compiler-error-c3846"></a>編譯器錯誤 C3846

' symbol '：無法從 ' assembly2 ' 匯入符號：因為 ' symbol ' 已從另一個元件 ' assembly1 ' 匯入

無法從參考的元件匯入符號，因為它先前是從參考的元件匯入。

## <a name="example"></a>範例

下列範例會產生 C3846：

```cpp
// C3846a.cpp
// compile with: /LD /clr
public ref struct G
{
};
```

然後編譯它：

```cpp
// C3846b.cpp
// compile with: /clr
#using "c3846a.dll"
#using "c3846a.obj"   // C3846

int main()
{
}
```
