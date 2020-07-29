---
title: 編譯器錯誤 C3482
ms.date: 11/04/2016
f1_keywords:
- C3482
helpviewer_keywords:
- C3482
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
ms.openlocfilehash: 0463f6de51e324bd02c8b766fd39909ee2803ecd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212575"
---
# <a name="compiler-error-c3482"></a>編譯器錯誤 C3482

'this' 在非靜態成員函式內只能做為 Lambda 擷取

您無法將傳遞 **`this`** 至在靜態方法或全域函式中宣告之 lambda 運算式的 capture 清單。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 將封入函式轉換成非靜態方法，或

- **`this`** 從 lambda 運算式的 capture 清單中移除指標。

## <a name="example"></a>範例

下列範例會產生 C3482：

```cpp
// C3482.cpp
// compile with: /c

class C
{
public:
   static void staticMethod()
   {
      [this] {}(); // C3482
   }
};
```

## <a name="see-also"></a>另請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)
