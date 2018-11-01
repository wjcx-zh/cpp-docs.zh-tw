---
title: 專案建置錯誤 PRJ0031
ms.date: 11/04/2016
f1_keywords:
- PRJ0031
helpviewer_keywords:
- PRJ0031
ms.assetid: b42435c6-e570-4f8e-9ad5-12a7ea69ccb2
ms.openlocfilehash: e5edae0c1b7464e4a3a5e9523332ce956d0dcf92
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648587"
---
# <a name="project-build-error-prj0031"></a>專案建置錯誤 PRJ0031

'Macro_expansion' 到檔案 'file' 包含 'macro' 而它評估步驟針對自訂建置的 '輸出' 屬性。

自訂建置步驟上的檔案有可能是因為巨集評估問題的錯誤輸出。 這項錯誤也可能表示，格式不正確的路徑，是包含字元或在檔案路徑中不合法的字元的組合。

若要解決這個錯誤，修正巨集或修正的路徑規格。 評估的路徑是從專案目錄的絕對路徑。