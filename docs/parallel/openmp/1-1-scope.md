---
title: 1.1 範圍 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a8570a3c-1dd6-4c3d-b368-a10fcb3534a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 48d14ec722299a9ff72ad5bab0a68cde5e00d6ad
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="11-scope"></a>1.1 範圍
此規格涵蓋只有使用者導向平行化作業，其中使用者明確地指定才能以平行方式執行程式的編譯器和執行階段系統所採取的動作。 OpenMP C 和 c + + 實作不需要檢查有相依性、 衝突、 死結、 競爭情形或其他問題，導致不正確的程式執行。 使用者負責確保使用 OpenMP C 和 c + + 應用程式開發介面建構的應用程式會正確執行。 本文件未涵蓋編譯器產生的自動平行處理和編譯器指示詞，以協助這類平行化作業。