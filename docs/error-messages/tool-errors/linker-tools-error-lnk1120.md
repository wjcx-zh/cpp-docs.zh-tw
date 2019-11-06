---
title: 連結器工具錯誤 LNK1120
description: 描述 LNK1120 連結器錯誤，它會報告連結中未解析的外部符號錯誤數目。
ms.date: 10/31/2019
f1_keywords:
- LNK1120
helpviewer_keywords:
- LNK1120
ms.assetid: 56aa7d36-921f-4daf-b44d-cca0d4fb1b51
ms.openlocfilehash: 21a1ede07a69cdc065dd897715e243115529600d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626574"
---
# <a name="linker-tools-error-lnk1120"></a>連結器工具錯誤 LNK1120

> *數位*無法解析的外部

錯誤 LNK1120 報告目前連結中[無法解析的外部符號](linker-tools-error-lnk2001.md#what-is-an-unresolved-external-symbol)錯誤數目。

每個未解析的外部符號會先由[LNK2001](linker-tools-error-lnk2001.md)或[LNK2019](linker-tools-error-lnk2019.md)錯誤報表。 LNK1120 訊息最後會出現，並顯示無法解析的符號錯誤計數。

> [!IMPORTANT]
> **您不需要修正此錯誤。** 當您在組建輸出中更正所有 LNK2001 和 LNK2019 連結器錯誤之前，這個錯誤就會消失。 一律從第一個回報的錯誤開始修正問題。 較早的錯誤可能是由先前的錯誤所造成，當先前的錯誤修正時，就會消失。
