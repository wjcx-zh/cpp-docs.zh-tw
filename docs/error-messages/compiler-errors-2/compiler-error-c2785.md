---
title: 編譯器錯誤 C2785
ms.date: 11/04/2016
f1_keywords:
- C2785
helpviewer_keywords:
- C2785
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
ms.openlocfilehash: 6aff2e5c96e3c79fc748d8a95779d6a08647ab03
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739619"
---
# <a name="compiler-error-c2785"></a>編譯器錯誤 C2785

' 宣告 1> ' 和 ' 宣告 2> ' 有不同的傳回類型

函式樣板特製化的傳回型別與主要函式範本的傳回型別不同。

### <a name="to-correct-this-error"></a>若要改正這項錯誤

1. 檢查函式範本的所有特製化是否一致。

## <a name="example"></a>範例

下列範例會產生 C2785：

```cpp
// C2785.cpp
// compile with: /c
template<class T> void f(T);

template<> int f(int); // C2785
template<> void f(int); // OK
```
