---
title: 專案建置錯誤 PRJ0033
ms.date: 11/04/2016
f1_keywords:
- PRJ0033
helpviewer_keywords:
- PRJ0033
ms.assetid: 84d4a052-0586-4b78-9315-81c1e8386c1e
ms.openlocfilehash: e074ee18508271b56686aa16f9012085ed3bd77d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346917"
---
# <a name="project-build-error-prj0033"></a>專案建置錯誤 PRJ0033

'Macro_expansion' 到檔案 'file' 包含 'macro' 而它評估步驟自訂建置的 '其他相依性' 屬性。

自訂建置步驟上的檔案中包含它可能是因為巨集評估問題的其他相依性中的錯誤。 這項錯誤也可能表示，格式不正確的路徑，是包含字元或在檔案路徑中不合法的字元的組合。

若要解決這個錯誤，修正巨集或修正的路徑規格。 評估的路徑是從專案目錄的絕對路徑。