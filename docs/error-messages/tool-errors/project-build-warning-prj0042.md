---
title: 專案建置警告 PRJ0042 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0042
dev_langs:
- C++
helpviewer_keywords:
- PRJ0042
ms.assetid: 682c9999-6f85-409f-b102-00c93243f74f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 260da8ac336c640ea875610b2c62e6c42c7d335e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211346"
---
# <a name="project-build-warning-prj0042"></a>專案建置警告 PRJ0042

> 檔案的自訂建置步驟的 '輸出屬性'*檔案*' 未設定。 將略過自訂建置步驟。

未執行自訂建置步驟，因為未指定輸出。

若要解決這個錯誤，請執行下列：

- 從組建中排除之自訂建置步驟。

- 加入輸出。

- 刪除自訂建置步驟之命令的內容。