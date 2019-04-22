---
title: 編譯器錯誤 C3481
ms.date: 11/04/2016
f1_keywords:
- C3481
helpviewer_keywords:
- C3481
ms.assetid: 5d09375a-5ed3-4b61-86ed-45e91fd734c7
ms.openlocfilehash: eff7c7a4f39524aa1d894b7b4590aa809714aae6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041198"
---
# <a name="compiler-error-c3481"></a>編譯器錯誤 C3481

'var': 找不到 Lambda 擷取變數

編譯器找不到傳遞至 Lambda 運算式擷取清單的變數定義。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 請從 Lambda 運算式的擷取清單移除變數。

## <a name="example"></a>範例

下例會產生 C3481，因為未定義變數 `n` ：

```
// C3481.cpp

int main()
{
   [n] {}(); // C3481
}
```

## <a name="see-also"></a>另請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)