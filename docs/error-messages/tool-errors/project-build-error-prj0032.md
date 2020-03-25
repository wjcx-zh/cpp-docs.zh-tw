---
title: 專案建置錯誤 PRJ0032
ms.date: 11/04/2016
f1_keywords:
- PRJ0032
helpviewer_keywords:
- PRJ0032
ms.assetid: bc6acbea-4041-4237-8b5a-f0434705d89f
ms.openlocfilehash: 62efa0e72c6fbe4bd38983ff0507923392427c04
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192480"
---
# <a name="project-build-error-prj0032"></a>專案建置錯誤 PRJ0032

專案層級自訂群組建步驟的 ' output ' 屬性包含 ' macro '，其會評估為 ' macro_expansion '。

專案上的自訂群組建步驟有不正確的輸出，可能是因為宏評估問題。 此錯誤也可能表示路徑格式不正確，其中包含檔案路徑中不合法的字元或字元組合。

若要解決這個錯誤，請修正宏或修正路徑規格。 評估的路徑是來自專案目錄的絕對路徑。
