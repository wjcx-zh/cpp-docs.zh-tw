---
title: "專案建置錯誤 PRJ0033 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0033
dev_langs: C++
helpviewer_keywords: PRJ0033
ms.assetid: 84d4a052-0586-4b78-9315-81c1e8386c1e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0cd7bcc0239ce88a19ae6009195f120a88be59ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0033"></a>專案建置錯誤 PRJ0033
自訂建置的 '其他相依性' 屬性 'macro_expansion' 跳檔案 'file' 包含 '巨集' 而它評估。  
  
 自訂建置步驟的檔案中包含錯誤可能是因為巨集評估問題的其他相依性。 這項錯誤也可能表示的格式不正確的路徑，是包含字元或檔案路徑中不合法的字元的組合。  
  
 若要解決這個錯誤，請修正巨集，或修正路徑規格。 評估的路徑是從專案目錄的絕對路徑。