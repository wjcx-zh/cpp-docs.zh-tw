---
title: 專案建置錯誤 PRJ0033 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0033
dev_langs:
- C++
helpviewer_keywords:
- PRJ0033
ms.assetid: 84d4a052-0586-4b78-9315-81c1e8386c1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2722bc53fe267d3327f265578435cb672c58d3f4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="project-build-error-prj0033"></a>專案建置錯誤 PRJ0033
自訂建置的 '其他相依性' 屬性 'macro_expansion' 跳檔案 'file' 包含 '巨集' 而它評估。  
  
 自訂建置步驟的檔案中包含錯誤可能是因為巨集評估問題的其他相依性。 這項錯誤也可能表示的格式不正確的路徑，是包含字元或檔案路徑中不合法的字元的組合。  
  
 若要解決這個錯誤，請修正巨集，或修正路徑規格。 評估的路徑是從專案目錄的絕對路徑。