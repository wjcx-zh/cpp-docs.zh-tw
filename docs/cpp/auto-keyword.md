---
title: auto 關鍵字
ms.date: 11/04/2016
ms.assetid: 744a41c0-2510-4140-a1be-96257e722908
ms.openlocfilehash: 3477bd5033fac5b69733db5d6095c1317aac42ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62284719"
---
# <a name="auto-keyword"></a>auto 關鍵字

**自動**關鍵字是宣告指定名稱。 不過，C++ 標準為此關鍵字定義了原始和修訂的意義。 視覺效果之前C++2010年**自動**關鍵字會宣告中的變數*自動*儲存類別，也就是具有區域存留期的變數。 從視覺效果C++2010年**自動**關鍵字宣告的類型推算自其宣告中的初始化運算式的變數。 [/Zc: auto&#91;-&#93; ](../build/reference/zc-auto-deduce-variable-type.md)編譯器選項可控制的意義**自動**關鍵字。

## <a name="syntax"></a>語法

```cpp
auto declarator ;
auto declarator initializer;
```

## <a name="remarks"></a>備註

定義**自動**關鍵字中變更C++程式設計語言，而不是在 C 程式設計語言。

下列主題將描述**自動**關鍵字和對應的編譯器選項：

- [自動](../cpp/auto-cpp.md)描述的新定義**自動**關鍵字。

- [/Zc: auto （推算變數類型）](../build/reference/zc-auto-deduce-variable-type.md)描述編譯器選項會告訴編譯器的定義**自動**關鍵字，才能使用。

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)