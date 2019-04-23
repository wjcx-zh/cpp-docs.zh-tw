---
title: 編譯器錯誤 C3530
ms.date: 11/04/2016
f1_keywords:
- C3530
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
ms.openlocfilehash: dd4368faaf323a75116128ec3a47666260436fce
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029115"
---
# <a name="compiler-error-c3530"></a>編譯器錯誤 C3530

'auto' 無法與任何其他類型規範結合

類型規範搭配`auto`關鍵字。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 請勿使用型別規範中使用的變數宣告`auto`關鍵字。

## <a name="example"></a>範例

下列範例會產生 C3530，因為變數`x`同時與宣告`auto`關鍵字和類型`int`，因為此範例會使用編譯 **/zc: auto**。

```
// C3530.cpp
// Compile with /Zc:auto
int main()
{
   auto int x;   // C3530
   return 0;
}
```

## <a name="see-also"></a>另請參閱

[auto 關鍵字](../../cpp/auto-keyword.md)