---
title: 編譯器錯誤 C2026 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2026
dev_langs:
- C++
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 055ac47d036a1027817aa6b3433bfe0e2e88570e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019545"
---
# <a name="compiler-error-c2026"></a>編譯器錯誤 C2026

字串太大，尾端字元已經截斷

字串的長度超過 16380 的單一位元組字元的限制。

再進行串連相鄰的字串，字串不能超過 16380 的單一位元組字元。

這個長度大約一半的 Unicode 字串也會產生這個錯誤。

如果您有定義，如下所示的字串，它會產生 C2026:

```
char sz[] =
"\
imagine a really, really \
long string here\
";
```

您無法分解，如下所示：

```
char sz[] =
"\
imagine a really, really "
"long string here\
";
```

您可以在自訂資源或外部檔案來儲存極大的字串常值 （32k 以上）。 請參閱[建立新的自訂或資料資源](../../windows/creating-a-new-custom-or-data-resource.md)如需詳細資訊。