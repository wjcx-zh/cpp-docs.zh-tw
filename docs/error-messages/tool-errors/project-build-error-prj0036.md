---
title: 專案建置錯誤 PRJ0036
ms.date: 11/04/2016
f1_keywords:
- PRJ0036
helpviewer_keywords:
- PRJ0036
ms.assetid: ee215cd1-2d66-474d-9a63-b9096f1c4923
ms.openlocfilehash: 67a225f907d06cd240ec2ebef236c0b4e0b849e2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192092"
---
# <a name="project-build-error-prj0036"></a>專案建置錯誤 PRJ0036

Web 部署工具的 [其他檔案] 屬性包含不正確專案。

[Web 部署] 屬性頁上的 [其他檔案] 屬性包含錯誤，可能是因為宏評估問題。 此錯誤也可能表示路徑格式不正確，其中包含檔案路徑中不合法的字元或字元組合。

若要解決這個錯誤，請修正宏或修正路徑規格。 評估的路徑是來自專案目錄的絕對路徑。

此錯誤也可能表示其中一個參考的檔案不存在。
