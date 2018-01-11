---
title: "專案建置錯誤 PRJ0031 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0031
dev_langs: C++
helpviewer_keywords: PRJ0031
ms.assetid: b42435c6-e570-4f8e-9ad5-12a7ea69ccb2
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9f1c07145f42e1ad71fb6c2a3542d9014b7e33b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0031"></a>專案建置錯誤 PRJ0031
自訂建置的 '輸出' 屬性 'macro_expansion' 跳檔案 'file' 包含 '巨集' 而它評估。  
  
 自訂建置步驟的檔案有可能是因為巨集評估問題的錯誤輸出。 這項錯誤也可能表示的格式不正確的路徑，是包含字元或檔案路徑中不合法的字元的組合。  
  
 若要解決這個錯誤，請修正巨集，或修正路徑規格。 評估的路徑是從專案目錄的絕對路徑。