---
title: 編譯器錯誤 C2483
ms.date: 09/15/2017
f1_keywords:
- C2483
helpviewer_keywords:
- C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
ms.openlocfilehash: 20b08c0d2cd89224ed3d3b8b34915deb947b0b4b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205110"
---
# <a name="compiler-error-c2483"></a>編譯器錯誤 C2483

>'*identifier*'：具有函數或析構函式的物件不可以宣告為 ' thread '

此錯誤訊息在 Visual Studio 2015 和更新版本中已過時。 在舊版中，使用 `thread` 屬性宣告的變數無法以需要執行時間評估的函式或其他運算式進行初始化。 必須要有靜態運算式，才能初始化 `thread` 資料。

## <a name="example"></a>範例

下列範例會在 Visual Studio 2013 和較早的版本中產生 C2483。

```cpp
// C2483.cpp
// compile with: /c
__declspec(thread) struct A {
   A(){}
   ~A(){}
} aa;   // C2483 error

__declspec(thread) struct B {} b;   // OK
```

## <a name="see-also"></a>另請參閱

[thread](../../cpp/thread.md)
