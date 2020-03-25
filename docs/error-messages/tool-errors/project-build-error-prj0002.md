---
title: 專案建置錯誤 PRJ0002
ms.date: 08/27/2018
f1_keywords:
- PRJ0002
helpviewer_keywords:
- PRJ0002
ms.assetid: 1c820b1f-9a24-4681-80ed-4fcbfd7caa00
ms.openlocfilehash: 30680f5b26f3be5e7f9b48d18e82fca42ed65493
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192935"
---
# <a name="project-build-error-prj0002"></a>專案建置錯誤 PRJ0002

> 從 '*命令列*' 傳回的錯誤結果。

從 [**屬性頁**] 對話方塊中的使用者輸入所形成的命令*行*，會傳回錯誤碼，但**輸出**視窗中不會顯示任何資訊。

此錯誤的解決方式取決於產生錯誤的工具。 針對 MIDL，如果已定義/o （重新導向輸出），您將會瞭解發生錯誤的原因。

無法取得失敗狀況相關資訊的批次檔（例如自訂群組建步驟或組建事件）也可能是此錯誤的原因。
