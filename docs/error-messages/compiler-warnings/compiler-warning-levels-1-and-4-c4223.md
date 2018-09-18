---
title: 編譯器警告 （層級 1 和 4） C4223 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4223
dev_langs:
- C++
helpviewer_keywords:
- C4223
ms.assetid: 6fc44336-0250-4432-928b-fc5dbe7b7c1c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a04ccf80bac123a3d2c6f28a063c274fe40a7e58
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075430"
---
# <a name="compiler-warning-levels-1-and-4-c4223"></a>編譯器警告 (層級 1 和 4) C4223

使用非標準擴充： 非左值陣列轉換為指標

在標準 C 中，您無法轉換為非左值陣列的指標。 使用預設的 Microsoft 擴充功能 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))，您可以。