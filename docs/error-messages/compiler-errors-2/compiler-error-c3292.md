---
title: 編譯器錯誤 C3292 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3292
dev_langs:
- C++
helpviewer_keywords:
- C3292
ms.assetid: ead485cc-5471-4e10-b361-300589ff5b70
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8fc5f89978a7ecaff526fa05ca7a47494aada987
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112456"
---
# <a name="compiler-error-c3292"></a>編譯器錯誤 C3292

無法重新開啟 cli 命名空間

無法在程式碼中宣告 cli 命名空間。  如需詳細資訊，請參閱 < [Platform、 default 和 cli 命名空間](../../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3292：

```
// C3292.cpp
// compile with: /clr /c
namespace cli {};   // C3292
```