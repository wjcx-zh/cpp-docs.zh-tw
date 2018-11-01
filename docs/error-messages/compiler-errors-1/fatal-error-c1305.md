---
title: 嚴重錯誤 C1305
ms.date: 11/04/2016
f1_keywords:
- C1305
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
ms.openlocfilehash: d67f0eabfd0718d8a3e3dd75e96c3e6c0d2266b6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623206"
---
# <a name="fatal-error-c1305"></a>嚴重錯誤 C1305

分析資料庫 'pgd_file' 適用於不同的架構

針對其他平台已傳遞至 /ltcg: pginstrument 作業所產生的.pgd 檔[/ltcg: pgoptimize](../../build/reference/ltcg-link-time-code-generation.md) 。 [特性指引最佳化](../../build/reference/profile-guided-optimizations.md)適用於 x86 和 x64 平台。 不過，以一個平台的 /ltcg: pginstrument 作業產生的.pgd 檔無效，無法做為輸入至 /ltcg: pgoptimize，適用於不同平台。

若要解決這個錯誤，只傳遞使用 /ltcg: pginstrument 至 /ltcg: pgoptimize 相同的平台上建立的.pgd 檔。