---
title: 專案建置警告 PRJ0029 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0029
dev_langs:
- C++
helpviewer_keywords:
- PRJ0029
ms.assetid: f02c09c6-09f3-4d44-8cd4-9a25336be1ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd6e7b738785d9cfacfb2128e03d3a3123da4fa1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320215"
---
# <a name="project-build-warning-prj0029"></a>專案建置警告 PRJ0029
專案層級自訂建置步驟的 '輸出' 屬性未設定。 將略過自訂建置步驟。  
  
 未執行自訂建置步驟，因為未指定輸出。  
  
 若要解決這個錯誤，執行下列動作：  
  
-   從組建排除自訂建置步驟。  
  
-   加入輸出。  
  
-   刪除自訂建置步驟之命令的內容。