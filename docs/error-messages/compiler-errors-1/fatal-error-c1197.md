---
title: 嚴重錯誤 C1197
ms.date: 11/04/2016
f1_keywords:
- C1197
helpviewer_keywords:
- C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
ms.openlocfilehash: 7f698262c73f0b311a92a8940107b552430919bb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747237"
---
# <a name="fatal-error-c1197"></a>嚴重錯誤 C1197

無法參考 ' mscorlib.dll. dll_1 '，因為程式已經參考 ' mscorlib.dll. dll_2 '

編譯器會與 common language runtime 的版本相符。  不過，嘗試從舊版本參考 common language runtime 檔案的版本。

若要解決這個錯誤，請只從您用來編譯的視覺效果C++版本所隨附的 common language runtime 版本參考檔案。

## <a name="example"></a>範例

下列範例會產生 C1197：

```cpp
// C1197.cpp
// compile with: /clr /c
// processor: x86
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197
// try the following line instead
// #using "mscorlib.dll"
```
