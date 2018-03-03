---
title: "專案建置錯誤 PRJ0003 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0003
dev_langs:
- C++
helpviewer_keywords:
- PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bcf80eb4d45fe1ae163772b96339c123996ae377
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="project-build-error-prj0003"></a>專案建置錯誤 PRJ0003  
  
> 錯誤繁衍 （spawn) '*命令列*'。  
  
*命令列*命令內輸入形成的**屬性頁**對話方塊傳回的錯誤碼，但會顯示任何資訊**輸出**視窗。  

此錯誤的可能原因包括：  
  
-   您的專案相依於 ATL Server。 從 Visual Studio 2008 中，ATL Server 已不再包含在 Visual Studio 中，但在 CodePlex 上的共用來源專案已發行。 若要下載的 ATL Server 的原始碼及工具，請移至[ATL 伺服器程式庫和工具](http://go.microsoft.com/fwlink/p/?linkid=81979)。  
  
-   系統資源不足。 關閉一些應用程式，以解決此問題。  
  
-   安全性權限不足。 請確認您有足夠的安全性權限。  
  
-   中指定的可執行檔路徑**VC + + 目錄**不包含您嘗試執行此工具的路徑。 如需資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)  
  
-   Makefile 專案遺漏上執行的命令**建置命令列**或**重建命令列**。  
  
## <a name="see-also"></a>請參閱  
 [專案建置錯誤和警告 (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)