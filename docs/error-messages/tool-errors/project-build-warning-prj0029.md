---
title: "專案建置警告 PRJ0029 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0029
dev_langs: C++
helpviewer_keywords: PRJ0029
ms.assetid: f02c09c6-09f3-4d44-8cd4-9a25336be1ea
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 924b37c40ee8b008fbf0a10896ef53e51fcbcc0a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-warning-prj0029"></a>專案建置警告 PRJ0029
專案層級自訂建置步驟的 '輸出' 屬性未設定。 將略過自訂建置步驟。  
  
 未執行自訂建置步驟，因為未指定輸出。  
  
 若要解決這個錯誤，執行下列動作：  
  
-   從組建排除自訂建置步驟。  
  
-   加入輸出。  
  
-   刪除自訂建置步驟之命令的內容。