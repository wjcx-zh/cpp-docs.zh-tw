---
title: 嚴重錯誤 C1103
ms.date: 11/04/2016
f1_keywords:
- C1103
helpviewer_keywords:
- C1103
ms.assetid: 9d276939-9c47-4235-9d20-76b8434f9731
ms.openlocfilehash: b6253af9fcf400321fb58d4d8a6d7aacf461b926
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174194"
---
# <a name="fatal-error-c1103"></a>嚴重錯誤 C1103

匯入 progid 時發生嚴重錯誤: 'message'

編譯器偵測到匯入類型程式庫時發生問題。  例如，您無法使用 progid 來指定類型程式庫，同時又指定 `no_registry`。

如需詳細資訊，請參閱 < [#import 指示詞](../../preprocessor/hash-import-directive-cpp.md)。

下列範例會產生 C1103：

```
// C1103.cpp
#import "progid:a.b.id.1.5" no_registry auto_search   // C1103
```