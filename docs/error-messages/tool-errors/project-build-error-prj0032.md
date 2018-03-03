---
title: "專案建置錯誤 PRJ0032 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0032
dev_langs:
- C++
helpviewer_keywords:
- PRJ0032
ms.assetid: bc6acbea-4041-4237-8b5a-f0434705d89f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 92497027db3a2449914696f03fc86a144a48b62e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0032"></a>專案建置錯誤 PRJ0032
專案層級自訂建置步驟的 '輸出' 屬性包含 '巨集'，它評估成 'macro_expansion'。  
  
 在專案上的自訂建置步驟有可能是因為巨集評估問題的錯誤輸出。 這項錯誤也可能表示的格式不正確的路徑，是包含字元或檔案路徑中不合法的字元的組合。  
  
 若要解決這個錯誤，請修正巨集，或修正路徑規格。 評估的路徑是從專案目錄的絕對路徑。