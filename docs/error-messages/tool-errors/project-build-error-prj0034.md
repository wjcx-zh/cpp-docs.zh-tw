---
title: 專案建置錯誤 PRJ0034
ms.date: 11/04/2016
f1_keywords:
- PRJ0034
helpviewer_keywords:
- PRJ0034
ms.assetid: 1da4a55b-231b-4476-8545-6997628fbc00
ms.openlocfilehash: bcb7e22d6a09e3435eb2236532101a1836c08a03
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192182"
---
# <a name="project-build-error-prj0034"></a>專案建置錯誤 PRJ0034

專案層級自訂群組建步驟的 [其他相依性] 屬性包含「宏」，其評估為 ' macro_expansion '。

專案上的自訂群組建步驟在其額外相依性中包含錯誤，可能是因為宏評估問題。 此錯誤也可能表示路徑格式不正確，其中包含檔案路徑中不合法的字元或字元組合。

若要解決這個錯誤，請修正宏或修正路徑規格。 評估的路徑是來自專案目錄的絕對路徑。
