---
title: 專案建置錯誤 PRJ0032
ms.date: 11/04/2016
f1_keywords:
- PRJ0032
helpviewer_keywords:
- PRJ0032
ms.assetid: bc6acbea-4041-4237-8b5a-f0434705d89f
ms.openlocfilehash: f1f292f3979c993a8fa8cb8ff44653ac7124b121
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344350"
---
# <a name="project-build-error-prj0032"></a>專案建置錯誤 PRJ0032

專案層級自訂建置步驟的 'Outputs' 屬性包含 'macro'，而它評估 'macro_expansion'。

在專案上的自訂建置步驟有可能是因為巨集評估問題的錯誤輸出。 這項錯誤也可能表示，格式不正確的路徑，是包含字元或在檔案路徑中不合法的字元的組合。

若要解決這個錯誤，修正巨集或修正的路徑規格。 評估的路徑是從專案目錄的絕對路徑。