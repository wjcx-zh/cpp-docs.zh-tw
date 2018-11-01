---
title: 1.1 範圍
ms.date: 11/04/2016
ms.assetid: a8570a3c-1dd6-4c3d-b368-a10fcb3534a6
ms.openlocfilehash: f87f631ae2d36662daa2ece4790170c00c5cbeb3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449201"
---
# <a name="11-scope"></a>1.1 範圍

此規格說明僅使用者導向平行化作業，其中使用者明確地指定才能以平行方式執行程式，編譯器和執行階段系統所採取的動作。 OpenMP C 和 c + + 實作不需要檢查相依性、 衝突、 死結、 競爭條件或不正確的程式執行會導致其他問題。 使用者負責確保使用 OpenMP C 和 c + + API 建構的應用程式正確執行。 本文件未涵蓋編譯器所產生的自動平行處理和編譯器指示詞，來協助這類的平行處理。