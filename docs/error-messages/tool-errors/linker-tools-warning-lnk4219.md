---
title: 連結器工具警告 LNK4219
ms.date: 11/04/2016
f1_keywords:
- LNK4219
helpviewer_keywords:
- LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
ms.openlocfilehash: 4488539a4f7282180048f1e3530e62e35c3b339e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183094"
---
# <a name="linker-tools-warning-lnk4219"></a>連結器工具警告 LNK4219

修復名稱修復溢位。 目標 ' 目標符號名稱 ' 超出範圍，正在插入 Thunk

連結器在位址或位移無法納入指定指令的情況下插入 Thunk，因為目標符號太遠超出指令的位置。

您可能想要重新排序影像（例如，使用[/order](../../build/reference/order-put-functions-in-order.md)選項），以避免額外的間接取值層級。
