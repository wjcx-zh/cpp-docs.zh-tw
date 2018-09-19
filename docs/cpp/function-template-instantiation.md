---
title: 函式樣板具現化 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- templates, instantiation
- function templates, instantiation
- instantiation, function templates
ms.assetid: f22a07c7-3ad1-465a-84f5-8737e274bd47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb94a54c4f99b79e3be742c5b1448151cff140c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116785"
---
# <a name="function-template-instantiation"></a>函式樣板具現化

先呼叫每種類型的函式樣板時，編譯器會建立具現化。 每次具現化都是一種為類型特製化樣板函式的版本。 每次為類型使用函式時，都會呼叫此具現化。 如果您有多個相同的具現化 (即使分屬不同模組)，可執行檔中只能有一個具現化複本。

任何引數和參數組合的函式樣板皆可進行函式引數轉換，前提是參數不可取決於該樣板引數。

以特定類型為引數宣告樣板，即可明確具現化該函式樣板。 例如，下列程式碼是可行的：

```cpp
// function_template_instantiation.cpp
template<class T> void f(T) { }

// Instantiate f with the explicitly specified template.
// argument 'int'
//
template void f<int> (int);

// Instantiate f with the deduced template argument 'char'.
template void f(char);
int main()
{
}
```

## <a name="see-also"></a>另請參閱

[函式樣板](../cpp/function-templates.md)