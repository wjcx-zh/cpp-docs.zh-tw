---
title: 編譯器錯誤 C3873
ms.date: 11/04/2016
f1_keywords:
- C3873
helpviewer_keywords:
- C3873
ms.assetid: e68fd3be-2391-492b-ac3f-d2428901b2e9
ms.openlocfilehash: ca70af12ef3223c8c5950f0fa98b1c63a2dd3a4c
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450817"
---
# <a name="compiler-error-c3873"></a>編譯器錯誤 C3873

'char'：識別項的第一個字元不可以是這個字元

C++ 編譯器會遵循 C++11 標準處理識別項中允許的字元。 識別項中只允許特定範圍的字元和通用字元名稱。 其他限制也適用於識別項的起始字元。 如需詳細資訊及允許的字元和通用字元名稱範圍清單，請參閱 [Identifiers](../../cpp/identifiers-cpp.md)。

編譯 C++/CLI 程式碼時，識別項中允許之字元範圍的限制較少。 在使用 /clr 所編譯的程式碼中的識別項應遵循[ECMA-335 標準：通用語言基礎結構 (CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm)。

下列範例會產生 C3873：

```
// C3873.cpp
int main() {
   int \u036F_abc;   // C3873, not in allowed range for initial character
   int abc_\u036F;   // OK, in allowed range for non-initial character
}
```