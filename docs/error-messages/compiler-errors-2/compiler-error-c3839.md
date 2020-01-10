---
title: 編譯器錯誤 C3839
ms.date: 11/04/2016
f1_keywords:
- C3839
helpviewer_keywords:
- C3839
ms.assetid: 0957faff-1e9f-439b-876b-85bd8d2c578d
ms.openlocfilehash: 19a1055a461d76856cc3bccbd9f8af0f0dcff356
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754923"
---
# <a name="compiler-error-c3839"></a>編譯器錯誤 C3839

無法變更 managed 或 WinRT 類型中的對齊

Managed 或 Windows 執行階段類型中的變數對齊是由 CLR 或 Windows 執行階段所控制，而且不能以[align](../../cpp/align-cpp.md)來修改。

下列範例會產生 C3839：

```cpp
// C3839a.cpp
// compile with: /clr
ref class C
{
public:
   __declspec(align(32)) int m_j; // C3839
};

int main()
{
}
```
