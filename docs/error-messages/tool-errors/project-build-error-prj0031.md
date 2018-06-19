---
title: 專案建置錯誤 PRJ0031 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0031
dev_langs:
- C++
helpviewer_keywords:
- PRJ0031
ms.assetid: b42435c6-e570-4f8e-9ad5-12a7ea69ccb2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d5ebd25c239a05c4300b574ec0d47035904187d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318317"
---
# <a name="project-build-error-prj0031"></a>專案建置錯誤 PRJ0031
自訂建置的 '輸出' 屬性 'macro_expansion' 跳檔案 'file' 包含 '巨集' 而它評估。  
  
 自訂建置步驟的檔案有可能是因為巨集評估問題的錯誤輸出。 這項錯誤也可能表示的格式不正確的路徑，是包含字元或檔案路徑中不合法的字元的組合。  
  
 若要解決這個錯誤，請修正巨集，或修正路徑規格。 評估的路徑是從專案目錄的絕對路徑。