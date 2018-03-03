---
title: "專案建置錯誤 PRJ0009 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0009
dev_langs:
- C++
helpviewer_keywords:
- PRJ0009
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0ee183c24cf330b54a335efbd0bbe2b00e18d209
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0009"></a>專案建置錯誤 PRJ0009
建置記錄檔無法開啟進行寫入。  
  
 **請確定檔案並未開啟另一個處理序，且沒有寫入保護。**  
  
 設定之後**建置記錄**屬性**是**且執行建立或重建，Visual c + + 無法以獨佔模式開啟建置記錄檔。  
  
 檢查**建置記錄**設定開啟**選項**對話方塊 (上**工具**功能表上，按一下 **選項**命令)，然後選取**VC + + 建置**中**專案**資料夾。 組建檔案在呼叫 BuildLog.htm，而且會寫入至中繼目錄 $(IntDir)。  
  
 此錯誤的可能原因：  
  
-   執行兩個處理序的 Visual c + + 和嘗試同時建置的相同專案中都相同的設定。  
  
-   鎖定檔案的處理序中開啟建置記錄檔。  
  
-   使用者沒有建立檔案的權限。  
  
-   目前的使用者檔案 BuildLog.htm 沒有寫入權限。