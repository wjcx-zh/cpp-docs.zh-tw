---
title: naked (C++)
ms.date: 11/04/2016
f1_keywords:
- naked_cpp
helpviewer_keywords:
- __declspec keyword [C++], naked
- naked __declspec keyword
ms.assetid: 69723241-05e1-439b-868e-20a83a16ab6d
ms.openlocfilehash: cfe3631086515e4e31c7d4188d46e3a7440662b7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177946"
---
# <a name="naked-c"></a>naked (C++)

**Microsoft 專屬**

對於以**naked**屬性宣告的函式，編譯器會產生不含初構和終解程式碼的程式碼。 利用此功能就可以使用內嵌組合語言程式碼撰寫您自己的初構/終解程式碼序列。 naked 函式在撰寫虛擬裝置驅動程式方面特別實用。  請注意， **naked**屬性僅適用于 X86 和 ARM，在 x64 上無法使用。

## <a name="syntax"></a>語法

```
__declspec(naked) declarator
```

## <a name="remarks"></a>備註

因為**naked**屬性只與函式的定義相關，而且不是類型修飾詞，所以 naked 函數必須使用擴充屬性語法和[__declspec](../cpp/declspec.md)關鍵字。

編譯器無法針對以 naked 屬性標記的函式產生內嵌函式，即使函式也以[__forceinline](inline-functions-cpp.md)關鍵字標記也一樣。

如果**naked**屬性套用至非成員方法定義以外的任何專案，則編譯器會發出錯誤。

## <a name="examples"></a>範例

此程式碼會定義具有**naked**屬性的函式：

```
__declspec( naked ) int func( formal_parameters ) {}
```

或者，或者：

```
#define Naked __declspec( naked )
Naked int func( formal_parameters ) {}
```

**Naked**屬性只會影響編譯器的初構和終解序列之程式碼產生的本質。 它不會影響針對呼叫這類函式所產生的程式碼。 因此， **naked**屬性不會被視為函式類型的一部分，而且函式指標不能有**naked**屬性。 此外， **naked**屬性無法套用至資料定義。 例如，此程式碼範例會產生錯誤：

```
__declspec( naked ) int i;
// Error--naked attribute not permitted on data declarations.
```

**Naked**屬性僅與函式的定義相關，而且不能在函數的原型中指定。 例如，此宣告會產生編譯器錯誤：

```
__declspec( naked ) int func();  // Error--naked attribute not permitted on function declarations
```

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[Naked 函式呼叫](../cpp/naked-function-calls.md)
