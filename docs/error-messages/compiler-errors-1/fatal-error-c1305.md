---
title: 嚴重錯誤 C1305
ms.date: 11/04/2016
f1_keywords:
- C1305
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
ms.openlocfilehash: 6ad00eb3d95e9f09d4f84daefb7e2a87fd1a3abf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203355"
---
# <a name="fatal-error-c1305"></a>嚴重錯誤 C1305

分析資料庫 ' pgd_file ' 適用于不同的架構

從另一個平臺的/LTCG： PGINSTRUMENT 作業產生的 .pgd 檔案已傳遞至[/ltcg： PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) 。 特性[指引優化](../../build/profile-guided-optimizations.md)適用于 x86 和 x64 平臺。 不過，使用一個平臺的/LTCG： PGINSTRUMENT 作業所產生的 .pgd 檔案，對於不同平臺的/LTCG： PGOPTIMIZE 輸入無效。

若要解決這個錯誤，請只將以/LTCG： PGINSTRUMENT 建立的 .pgd 檔案，傳遞至同一個平臺上的/LTCG： PGOPTIMIZE。
