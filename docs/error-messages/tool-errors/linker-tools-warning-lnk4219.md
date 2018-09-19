---
title: 連結器工具警告 LNK4219 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4219
dev_langs:
- C++
helpviewer_keywords:
- LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: daf097cd8715a7c523e6e8a2ea46714481ca7d2a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105204"
---
# <a name="linker-tools-warning-lnk4219"></a>連結器工具警告 LNK4219

修復名稱修復溢位。 目標 '目標 symbol name' 超出範圍，插入 thunk

連結器的情況下，其中的位址或位移無法放入指定的指示，因為目標符號太遠而從指示的位置，插入 thunk。

您可能想要重新排列映像 (使用[/order](../../build/reference/order-put-functions-in-order.md)選項，例如) 以避免額外的層級的間接取值。