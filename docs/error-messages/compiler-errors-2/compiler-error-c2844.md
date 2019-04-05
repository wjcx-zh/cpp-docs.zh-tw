---
title: 編譯器錯誤 C2844
ms.date: 11/04/2016
f1_keywords:
- C2844
helpviewer_keywords:
- C2844
ms.assetid: dcaf4cd2-21b0-4280-ae42-0a706c524d83
ms.openlocfilehash: 2676a32cee487595a2241359496ae9b0380126b8
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "58775007"
---
# <a name="compiler-error-c2844"></a>編譯器錯誤 C2844

'member': 不可以是成員的介面 'interface'

[介面類別](../../extensions/interface-class-cpp-component-extensions.md)不能包含資料成員，除非它還有一個屬性。

介面中不允許的屬性或成員函式以外的任何項目。 此外，不允許建構函式、 解構函式和運算子。

下列範例會產生 C2844:

```
// C2844a.cpp
// compile with: /clr /c
public interface class IFace {
   int i;   // C2844
   // try the following line instead
   // property int Size;
};
```
