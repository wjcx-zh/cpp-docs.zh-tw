---
title: "Visual c + + 應用程式部署至應用程式本機資料夾 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- deploying Visual C++ applications
ms.assetid: 47a81c47-9dbe-47c6-96cc-fbb2fda5e6ad
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1d9a92a5fef96932f1d6a58503fe6355b5a410ce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-deploying-a-visual-c-application-to-an-application-local-folder"></a>逐步解說：將 Visual C++ 應用程式部署至應用程式本機資料夾
描述如何部署 Visual c + + 應用程式檔案複製到其資料夾。  
  
## <a name="prerequisites"></a>必要條件  
  
-   已安裝 Visual Studio 的電腦。  
  
-   未安裝 Visual c + + 程式庫的另一部電腦。  
  
### <a name="to-deploy-an-application-to-an-application-local-folder"></a>若要在應用程式部署至應用程式的本機資料夾  
  
1.  建立並建置 MFC 應用程式所遵循的步驟[逐步解說： 部署 Visual c + + 應用程式所使用之安裝專案](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)。  
  
2.  複製適當的 MFC 和 C 執行階段 (CRT) 程式庫檔案 — 例如，適用於 x86 平台和 Unicode 支援、 複製 mfc100u.dll 和 msvcr100.dll 從 \Program Files\Microsoft Visual Studio 10.0\VC\redist\x86\—and 然後將它們貼 \Release\ 資料夾中您的 MFC 專案。 如需其他檔案，您可能必須將複製的詳細資訊，請參閱[判斷要轉散發哪些 Dll](../ide/determining-which-dlls-to-redistribute.md)。  
  
3.  在沒有 Visual c + + 程式庫第二部電腦上執行的 MFC 應用程式。  
  
    1.  複製 \Release\ 資料夾的內容，並將它們貼在第二部電腦上的應用程式資料夾中。  
  
    2.  在第二部電腦上執行應用程式。  
  
     應用程式執行成功，因為 Visual c + + 程式庫中可用的應用程式的本機資料夾。  
  
## <a name="see-also"></a>請參閱  
 [部署範例](../ide/deployment-examples.md)