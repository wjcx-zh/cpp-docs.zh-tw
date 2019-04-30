---
title: 連結器工具警告 LNK4219
ms.date: 11/04/2016
f1_keywords:
- LNK4219
helpviewer_keywords:
- LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
ms.openlocfilehash: 7407537b55525bf622fc11cdbdb8e00244e51c18
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410248"
---
# <a name="linker-tools-warning-lnk4219"></a>連結器工具警告 LNK4219

修復名稱修復溢位。 目標 '目標 symbol name' 超出範圍，插入 thunk

連結器的情況下，其中的位址或位移無法放入指定的指示，因為目標符號太遠而從指示的位置，插入 thunk。

您可能想要重新排列映像 (使用[/order](../../build/reference/order-put-functions-in-order.md)選項，例如) 以避免額外的層級的間接取值。