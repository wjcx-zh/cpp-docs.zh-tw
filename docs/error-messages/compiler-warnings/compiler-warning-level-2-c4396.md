---
title: 編譯器警告 (層級 2) C4396
ms.date: 11/04/2016
f1_keywords:
- C4396
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
ms.openlocfilehash: e874e00d44eef29240cca55541837facfcf64495
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052034"
---
# <a name="compiler-warning-level-2-c4396"></a>編譯器警告 (層級 2) C4396

'name' : 當 Friend 宣告參考函式樣板的特製化時，不能使用內嵌規範

函式樣板的特製化不能指定任何 [內嵌](../../cpp/inline-functions-cpp.md) 規範。 編譯器會發出警告 C4396 並忽略內嵌規範。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 請從 Friend 函式宣告移除 `inline`、 `__inline`或 `__forceinline` 規範。

## <a name="example"></a>範例

下列程式碼範例顯示無效的 Friend 函式宣告與 `inline` 規範。

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