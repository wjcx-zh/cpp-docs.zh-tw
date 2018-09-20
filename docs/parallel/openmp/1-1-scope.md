---
title: 1.1 範圍 |Microsoft Docs
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
ms.openlocfilehash: 81babf799860030f6d398f64b55ed65039de8649
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393525"
---
# <a name="11-scope"></a>1.1 範圍

此規格說明僅使用者導向平行化作業，其中使用者明確地指定才能以平行方式執行程式，編譯器和執行階段系統所採取的動作。 OpenMP C 和 c + + 實作不需要檢查相依性、 衝突、 死結、 競爭條件或不正確的程式執行會導致其他問題。 使用者負責確保使用 OpenMP C 和 c + + API 建構的應用程式正確執行。 本文件未涵蓋編譯器所產生的自動平行處理和編譯器指示詞，來協助這類的平行處理。