---
title: naked （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- naked_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], naked
- naked __declspec keyword
ms.assetid: 69723241-05e1-439b-868e-20a83a16ab6d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89ab41c396f8602d16e2b2d88c3d83aeb7cdf21a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018376"
---
# <a name="naked-c"></a>naked (C++)

**Microsoft 專屬**

針對以宣告的函式**naked**屬性，編譯器會產生不具初構和終解程式碼。 利用此功能就可以使用內嵌組合語言程式碼撰寫您自己的初構/終解程式碼序列。 naked 函式在撰寫虛擬裝置驅動程式方面特別實用。  請注意， **naked**屬性只適用於 x86 和 ARM，而且不提供 x64。

## <a name="syntax"></a>語法

```
__declspec(naked) declarator
```

## <a name="remarks"></a>備註

因為**naked**屬性，才會相關函式的定義，而且不是類型修飾詞，naked 函式必須使用擴充的屬性語法並[__declspec](../cpp/declspec.md)關鍵字。


編譯器無法產生內嵌函式標記為 naked 屬性中，函式，即使函式也標記著[__forceinline](inline-functions-cpp.md)關鍵字。

編譯器會發出錯誤，如果**naked**屬性會套用至非成員方法定義以外的任何項目。

## <a name="examples"></a>範例

此程式碼定義的函式**naked**屬性：

```
__declspec( naked ) int func( formal_parameters ) {}
```

或者，或者：

```
#define Naked __declspec( naked )
Naked int func( formal_parameters ) {}
```

**Naked**屬性會影響編譯器針對函式的初構和終解序列產生程式碼的本質。 它不會影響針對呼叫這類函式所產生的程式碼。 因此， **naked**屬性不會視為函式的型別部分，並不能有函式指標**naked**屬性。 此外， **naked**無法將屬性套用至資料定義。 例如，此程式碼範例會產生錯誤：

```
__declspec( naked ) int i;
// Error--naked attribute not permitted on data declarations.
```

**Naked**屬性是僅與函式定義相關，而且不能在函式的原型中指定。 比方說，這個宣告會產生編譯器錯誤：

```
__declspec( naked ) int func();  // Error--naked attribute not permitted on function declarations
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[Naked 函式呼叫](../cpp/naked-function-calls.md)