---
title: 編譯器錯誤 C3807
ms.date: 11/04/2016
f1_keywords:
- C3807
helpviewer_keywords:
- C3807
ms.assetid: 7e2b0aab-8c61-4e71-b9c1-fcaeb6a1b5ea
ms.openlocfilehash: b5599914666af95a29667acc1ad4ad35eef7608f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391929"
---
# <a name="compiler-error-c3807"></a>編譯器錯誤 C3807

'type': 具有 ComImport 屬性的類別不可衍生自 'type2'，允許只介面實作

衍生自類型<xref:System.Runtime.InteropServices.ComImportAttribute>只能實作一個介面。

## <a name="example"></a>範例

下列範例會產生 C3807。

```
// C3807.cpp
// compile with: /clr /c
ref struct S {};
interface struct I {};

[System::Runtime::InteropServices::ComImportAttribute()]
ref struct S1 : S {};   // C3807
ref struct S2 : I {};
```