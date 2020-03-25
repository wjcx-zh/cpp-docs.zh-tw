---
title: 編譯器錯誤 C3554
ms.date: 11/04/2016
f1_keywords:
- C3554
helpviewer_keywords:
- C3554
ms.assetid: aede18d5-fefc-4da9-9b69-adfe90bfa742
ms.openlocfilehash: ecdb90e845714e046ed21cf5a200ef4548487df6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200599"
---
# <a name="compiler-error-c3554"></a>編譯器錯誤 C3554

'decltype' 無法和任何其他型別規範結合

您不能限制 `decltype()` 關鍵字搭配任何類型規範。 例如，下列程式碼片段會產生錯誤 C3554。

```
int x;
unsigned decltype(x); // C3554
```
