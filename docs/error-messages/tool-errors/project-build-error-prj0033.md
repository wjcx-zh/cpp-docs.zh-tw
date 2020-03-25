---
title: 專案建置錯誤 PRJ0033
ms.date: 11/04/2016
f1_keywords:
- PRJ0033
helpviewer_keywords:
- PRJ0033
ms.assetid: 84d4a052-0586-4b78-9315-81c1e8386c1e
ms.openlocfilehash: 141355ac49ec4722e85b5d4c25240e8048a72c9a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192185"
---
# <a name="project-build-error-prj0033"></a>專案建置錯誤 PRJ0033

檔案 ' file ' 之自訂群組建步驟的 [其他相依性] 屬性包含會評估為 ' macro_expansion ' 的 ' 宏 '。

檔案的自訂群組建步驟在其額外相依性中包含錯誤，可能是因為宏評估問題。 此錯誤也可能表示路徑格式不正確，其中包含檔案路徑中不合法的字元或字元組合。

若要解決這個錯誤，請修正宏或修正路徑規格。 評估的路徑是來自專案目錄的絕對路徑。
