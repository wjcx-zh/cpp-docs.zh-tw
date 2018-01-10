---
title: "專案建置錯誤 PRJ0006 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0006
dev_langs: C++
helpviewer_keywords: PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 817450fb6b72f985d7ff49f7e65f9dfa0933b4d6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0006"></a>專案建置錯誤 PRJ0006
無法開啟暫存檔案 'file'。 請確定檔案存在，而且該目錄沒有寫入保護。  
  
 Visual c + + 建置程序期間無法建立暫存檔。 原因包括：  
  
-   沒有暫存目錄。  
  
-   唯讀的暫存目錄。  
  
-   磁碟空間不足。  
  
-   $ （intdir） 資料夾是唯讀，或包含處於唯讀狀態的暫存檔案。  
  
 這項錯誤也會發生下列錯誤 PRJ0007： 無法建立輸出目錄 'directory'。 錯誤 PRJ0007 表示無法建立 $ （intdir） 目錄，隱含建立的暫時檔案也會失敗。  
  
 每當您指定時，會建立暫存檔案：  
  
-   回應檔。  
  
-   自訂建置步驟。  
  
-   建置事件。