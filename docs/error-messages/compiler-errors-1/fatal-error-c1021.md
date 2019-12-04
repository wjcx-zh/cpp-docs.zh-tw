---
title: 嚴重錯誤 C1021
ms.date: 11/04/2016
f1_keywords:
- C1021
helpviewer_keywords:
- C1021
ms.assetid: e23171f4-ca6b-40c0-a913-a2edc6fa3766
ms.openlocfilehash: 861e768563cf737d6925d5753d80cd9269eff4fe
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756886"
---
# <a name="fatal-error-c1021"></a>嚴重錯誤 C1021

無效的前置處理器命令 'string'

`string` 不是有效的 [前置處理器指示詞](../../preprocessor/preprocessor-directives.md)。 若要解決這個錯誤，請使用 `string`的有效前置處理器名稱。

下列範例會產生 C1021：

```cpp
// C1021.cpp
#BadPreProcName    // C1021 delete line
```
