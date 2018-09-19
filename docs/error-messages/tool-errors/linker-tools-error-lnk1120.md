---
title: 連結器工具錯誤 LNK1120 |Microsoft Docs
ms.custom: ''
ms.date: 05/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1120
dev_langs:
- C++
helpviewer_keywords:
- LNK1120
ms.assetid: 56aa7d36-921f-4daf-b44d-cca0d4fb1b51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ea6cc7fdde3d68c9b00ba60c7fa650cbdfd3bd8d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086339"
---
# <a name="linker-tools-error-lnk1120"></a>連結器工具錯誤 LNK1120

> *數字*無法解析的外部符號

錯誤 LNK1120 報告計數 (*數字*) 的未解析外部符號錯誤，此連結作業。 大部分無法解析的外部符號錯誤會報告個別[連結器工具錯誤 LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)並[連結器工具錯誤 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)，這在之前針對每個無法解析的外部執行一次此錯誤訊息符號時發生錯誤。

若要修正這個錯誤，更正所有其他無法解析外部的錯誤或其他組建輸出中前面的連結器錯誤。 當還是不會有任何未解析的外部錯誤時，不會報告此錯誤。
