---
title: 專案建置錯誤 PRJ0036 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0036
dev_langs:
- C++
helpviewer_keywords:
- PRJ0036
ms.assetid: ee215cd1-2d66-474d-9a63-b9096f1c4923
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32b73fb8d86ff537912218ea35089382a93aec4c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065188"
---
# <a name="project-build-error-prj0036"></a>專案建置錯誤 PRJ0036

Web Deployment Tool 的 '其他檔案' 屬性包含無效的項目。

Web 部署的 [屬性] 頁面上的其他檔案屬性中包含的錯誤，可能是因為巨集評估問題。 這項錯誤也可能表示，格式不正確的路徑，是包含字元或在檔案路徑中不合法的字元的組合。

若要解決這個錯誤，修正巨集或修正的路徑規格。 評估的路徑是從專案目錄的絕對路徑。

這項錯誤也可能表示其中一個所參考的檔案不存在。