---
title: "專案建置錯誤 PRJ0002 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0002
dev_langs:
- C++
helpviewer_keywords:
- PRJ0002
ms.assetid: 1c820b1f-9a24-4681-80ed-4fcbfd7caa00
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 81d7f45fb2145d0f47716841a50c9320fd46833c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0002"></a>專案建置錯誤 PRJ0002
從 '命令列' 傳回錯誤結果。  
  
 命令，***命令列***，其中的格式正確，從使用者輸入中**屬性頁**對話方塊中，傳回錯誤碼，但沒有資訊會出現在 [輸出] 視窗。  
  
 此錯誤的解決方法取決於哪一種工具產生錯誤。 MIDL，您會了解發生了什麼錯誤如果定義 /o （重新導向輸出）。  
  
 批次檔，例如自訂建置步驟或建置事件，不是失敗狀況的相關資訊也可能是此錯誤的原因。