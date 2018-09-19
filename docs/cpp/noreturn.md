---
title: noreturn |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- noreturn_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6133fc70c5c2b8bb8f794746c1d5ca11be97b817
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031037"
---
# <a name="noreturn"></a>noreturn

## <a name="microsoft-specific"></a>Microsoft 特定的

這 **__declspec**屬性會告知編譯器函式不會傳回。 如此一來，編譯器知道呼叫的程式碼 **__declspec （noreturn)** 函式是不可能執行到。

如果編譯器發現某個函式包含的控制路徑不會傳回值，則會產生警告 (C4715) 或錯誤訊息 (C2202)。 如果無法連線的控制路徑，因為永遠不會傳回的函式，您可以使用 **__declspec （noreturn)** 若要避免這個警告或錯誤。

> [!NOTE]
>  新增 **__declspec （noreturn)** 預期會傳回的函式可能會導致未定義的行為。

## <a name="example"></a>範例

在下列範例中，**其他**子句不包含 return 陳述式。  宣告`fatal`作為 **__declspec （noreturn)** 可避免錯誤或警告訊息。

```cpp
// noreturn2.cpp
__declspec(noreturn) extern void fatal () {}

int main() {
   if(1)
     return 1;
   else if(0)
     return 0;
   else
     fatal();
}
```

## <a name="see-also"></a>另請參閱

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)