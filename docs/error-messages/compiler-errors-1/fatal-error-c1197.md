---
title: 嚴重錯誤 C1197 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1197
dev_langs:
- C++
helpviewer_keywords:
- C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 58561e7bd906fc750779ef53a4f68ec27088a3b7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024758"
---
# <a name="fatal-error-c1197"></a>嚴重錯誤 C1197

無法參考 'mscorlib.dll_1'，因為程式已經被參考 'mscorlib.dll_2'

編譯器會對應到 common language runtime 的版本。  不過，嘗試將參考從舊版的通用語言執行階段檔案的版本。

若要解決這個錯誤，只能參考來自隨附的 common language runtime 的版本，您會使用進行編譯的 Visual c + + 版本的檔案。

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