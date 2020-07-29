---
title: 編譯器警告 (層級 2) C4396
ms.date: 11/04/2016
f1_keywords:
- C4396
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
ms.openlocfilehash: fec6875fdb2e8a60e71fe08da1ed4e8fa82e4641
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87206038"
---
# <a name="compiler-warning-level-2-c4396"></a>編譯器警告 (層級 2) C4396

'name' : 當 Friend 宣告參考函式樣板的特製化時，不能使用內嵌規範

函式樣板的特製化不能指定任何 [內嵌](../../cpp/inline-functions-cpp.md) 規範。 編譯器會發出警告 C4396 並忽略內嵌規範。

### <a name="to-correct-this-error"></a>更正這個錯誤

- **`inline`** **`__inline`** **`__forceinline`** 從 friend 函式宣告中移除、或規範。

## <a name="example"></a>範例

下列程式碼範例顯示不正確 friend 函式宣告與 **`inline`** 規範。

```cpp
// C4396.cpp
// compile with: /W2 /c

class X;
template<class T> void Func(T t, int i);

class X {
    friend inline void Func<char>(char t, int i);  //C4396
// try the following line instead
//    friend void Func<char>(char t, int i);
    int i;
};
```
