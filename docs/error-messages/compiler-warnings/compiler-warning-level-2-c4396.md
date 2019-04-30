---
title: 編譯器警告 (層級 2) C4396
ms.date: 11/04/2016
f1_keywords:
- C4396
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
ms.openlocfilehash: 84045ea2c285be8b1c1c9d1fd62b417db00dd29c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402446"
---
# <a name="compiler-warning-level-2-c4396"></a>編譯器警告 (層級 2) C4396

'name' : 當 Friend 宣告參考函式樣板的特製化時，不能使用內嵌規範

函式樣板的特製化不能指定任何 [內嵌](../../cpp/inline-functions-cpp.md) 規範。 編譯器會發出警告 C4396 並忽略內嵌規範。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 請從 Friend 函式宣告移除 `inline`、 `__inline`或 `__forceinline` 規範。

## <a name="example"></a>範例

下列程式碼範例顯示無效的 Friend 函式宣告與 `inline` 規範。

```
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