---
title: 編譯器錯誤 C2026
ms.date: 11/04/2016
f1_keywords:
- C2026
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
ms.openlocfilehash: 9747b1edadc76ceeb502b2c6fd03496b91769f5a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208061"
---
# <a name="compiler-error-c2026"></a>編譯器錯誤 C2026

字串太大，尾端字元已截斷

字串長度超過16380個單一位元組字元的限制。

在串連連續的字串之前，字串的長度不能超過16380個單一位元組字元。

大約一半這個長度的 Unicode 字串也會產生這個錯誤。

如果您的字串定義如下，則會產生 C2026：

```
char sz[] =
"\
imagine a really, really \
long string here\
";
```

您可以如下所示加以分解：

```
char sz[] =
"\
imagine a really, really "
"long string here\
";
```

您可能想要在自訂資源或外部檔案中儲存非常大型的字串常值（32K 或以上）。 如需詳細資訊，請參閱[建立新的自訂或資料資源](../../windows/creating-a-new-custom-or-data-resource.md)。
