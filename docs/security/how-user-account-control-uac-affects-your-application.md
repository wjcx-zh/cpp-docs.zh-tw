---
title: "使用者帳戶控制 (UAC) 如何影響您的應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- UAC [C++]
- security [C++], User Account Control
- user accounts [C++]
- User Account Control [C++]
ms.assetid: 0d001870-253e-4989-b689-f78035953799
caps.latest.revision: "5"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e609c16d63974506a06d6ec553cf4be09509acb9
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="how-user-account-control-uac-affects-your-application"></a>使用者帳戶控制 (UAC) 如何影響應用程式
使用者帳戶控制 (UAC) 是 Windows Vista 的功能，可以讓使用者帳戶擁有有限的權限。 您可以在以下網站找到有關 UAC 的詳細資訊：  
  
-   [Windows Vista 使用者帳戶控制逐步指南](http://go.microsoft.com/fwlink/p/?linkid=53781)  
  
-   [開發人員最佳做法和最小權限環境中應用程式的指導方針](http://go.microsoft.com/fwlink/p/?linkid=82444)  
  
-   [了解和設定 Windows Vista 中的使用者帳戶控制](http://go.microsoft.com/fwlink/p/?linkid=82445)  
  
## <a name="building-projects-after-enabling-uac"></a>在啟用 UAC 後建置專案  
 如果您在停用 UAC 的情況下，在 Windows Vista 上建置 Visual C++ 專案，而且在稍後啟用了 UAC，就必須清除及重新建置專案，才能夠使其正確運作。  
  
## <a name="applications-that-require-administrative-privileges"></a>需要系統管理員權限的應用程式  
 根據預設，Visual C++ 連結器 (Linker) 會以 `asInvoker` 的執行層級，將 UAC 片段內嵌到應用程式的資訊清單中。 如果您的應用程式需要系統管理員權限才能正確執行 (例如，如果會修改登錄的 HKLM 節點，或是會寫入到磁碟上受保護的區域，如 Windows 目錄)，您就必須修改應用程式。  
  
 第一個選項是修改要變更的執行層級的資訊清單的 UAC 片段*requireAdministrator*。 然後，應用程式便會提示使用者，必須在執行前提供管理認證。 如需如何執行這項操作資訊，請參閱[/MANIFESTUAC （將 UAC 資訊內嵌資訊清單中）](../build/reference/manifestuac-embeds-uac-information-in-manifest.md)。  
  
 第二個選項是藉由指定不要內嵌到資訊清單的 UAC 片段**/manifestuac: no**連結器選項。 在此情況下，您的應用程式便會以虛擬化的方式執行。 您對登錄或檔案系統所做的任何變更，都不會在應用程式結束後持續。  
  
 下列流程圖描述應用程式將會如何根據是否有啟用 UAC，以及應用程式是否有 UAC 資訊清單來執行。  
  
 ![Windows Vista 載入器行為](media/uacflowchart.png "UACflowchart")  
  
## <a name="see-also"></a>請參閱  
 [安全性最佳做法](security-best-practices-for-cpp.md)