---
title: 編譯器錯誤 C3824
ms.date: 11/04/2016
f1_keywords:
- C3824
helpviewer_keywords:
- C3824
ms.assetid: b6c6adf1-0a29-401c-a06e-616fd50d4c37
ms.openlocfilehash: 78081de44a834b16d34d1f88a5dc996efb1f784c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220141"
---
# <a name="compiler-error-c3824"></a>編譯器錯誤 C3824

' member '：這個類型不能出現在此內容中（函式參數、傳回類型或靜態成員）

釘選指標不可以是函式參數、傳回類型或已宣告 **`static`** 。

## <a name="example"></a>範例

下列範例會產生 C3824：

```cpp
// C3824a.cpp
// compile with: /clr /c
void func() {
   static pin_ptr<int> a; // C3824
   pin_ptr<int> b; // OK
}
```
