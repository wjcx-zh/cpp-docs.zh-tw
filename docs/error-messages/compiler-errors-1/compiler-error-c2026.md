---
title: 編譯器錯誤 C2026
description: 描述 Microsoft C/c + + 編譯器錯誤 C2026、其原因和解決方式。
ms.date: 09/25/2020
f1_keywords:
- C2026
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
ms.openlocfilehash: 39195568f964f07c6131fa43ef4a0f06121795da
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414044"
---
# <a name="compiler-error-c2026"></a>編譯器錯誤 C2026

> 字串太大，已截斷尾端字元

字串的長度超過16380個單一位元組字元的限制。

## <a name="remarks"></a>備註

在串連連續的字串之前，字串的長度不能超過16380的單一位元組字元。

此長度大約有一半的 Unicode 字串也會產生此錯誤。

## <a name="example"></a>範例

如果您有定義如下的字串，它會產生 C2026：

```C
char sz[] =
"\
imagine a really, really \
long string here\
";
```

您可以依照下列方式將它中斷：

```C
char sz[] =
"\
imagine a really, really "
"long string here\
";
```

您可能會想要在自訂資源或外部檔案中儲存非常大型的字串常值， (32K 或更多的) 。 如需詳細資訊，請參閱 [建立新的自訂或資料資源](../../windows/binary-editor.md#to-create-a-new-custom-or-data-resource)。
