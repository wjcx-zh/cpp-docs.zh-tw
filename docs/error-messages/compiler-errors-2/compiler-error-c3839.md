---
title: 編譯器錯誤 C3839
ms.date: 11/04/2016
f1_keywords:
- C3839
helpviewer_keywords:
- C3839
ms.assetid: 0957faff-1e9f-439b-876b-85bd8d2c578d
ms.openlocfilehash: b8382213fbe7cc953dafd9610bfb993ba7837947
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613004"
---
# <a name="compiler-error-c3839"></a>編譯器錯誤 C3839

無法變更 managed 或 WinRT 類型中的對齊

變數的對齊方式在 managed 或 Windows 執行階段類型由 CLR 或 Windows 執行階段所控制，而且無法修改與[對齊](../../cpp/align-cpp.md)。

下列範例會產生 C3839：

```
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