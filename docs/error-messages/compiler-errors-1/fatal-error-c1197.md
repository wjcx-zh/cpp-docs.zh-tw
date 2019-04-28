---
title: 嚴重錯誤 C1197
ms.date: 11/04/2016
f1_keywords:
- C1197
helpviewer_keywords:
- C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
ms.openlocfilehash: e1c00a001c807b0cc6a5946b61ca4e9d5dc0167a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62229116"
---
# <a name="fatal-error-c1197"></a>嚴重錯誤 C1197

無法參考 'mscorlib.dll_1'，因為程式已經被參考 'mscorlib.dll_2'

編譯器會對應到 common language runtime 的版本。  不過，嘗試將參考從舊版的通用語言執行階段檔案的版本。

若要解決這個錯誤，只能參考檔案 」 從視覺效果的版本所隨附的 common language runtime 的版本C++您會使用進行編譯。

## <a name="example"></a>範例

下列範例會產生 C1197:

```
// C1197.cpp
// compile with: /clr /c
// processor: x86
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197
// try the following line instead
// #using "mscorlib.dll"
```