---
title: 將 Visual C++ 應用程式部署至應用程式本機資料夾 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deploying Visual C++ applications
ms.assetid: 47a81c47-9dbe-47c6-96cc-fbb2fda5e6ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a02e585dc2b82c8b8ad675907e4205db6ad7279
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "33337905"
---
# <a name="walkthrough-deploying-a-visual-c-application-to-an-application-local-folder"></a>逐步解說：將 Visual C++ 應用程式部署至應用程式本機資料夾
描述如何透過將檔案複製到其資料夾來部署 Visual C++ 應用程式。  
  
## <a name="prerequisites"></a>必要條件  
  
-   已安裝 Visual Studio 的電腦。  
  
-   沒有 Visual C++ 程式庫的另一部電腦。  
  
### <a name="to-deploy-an-application-to-an-application-local-folder"></a>將應用程式部署至應用程式本機資料夾  
  
1.  遵循[逐步解說：使用安裝專案部署 Visual C++ 應用程式](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)中的步驟，建立及建置 MFC 應用程式。  
  
2.  複製適當的 MFC 和 C 執行階段 (CRT) 程式庫檔案 (例如，針對 x86 平台和 Unicode 支援，請從 \Program Files\Microsoft Visual Studio 10.0\VC\redist\x86\ 複製 mfc100u.dll 和 msvcr100.dll)，然後貼到您 MFC 專案的 \Release\ 資料夾中。 如需您可能必須複製之其他檔案的詳細資訊，請參閱[決定要轉散發哪些 DLL](../ide/determining-which-dlls-to-redistribute.md)。  
  
3.  在沒有 Visual C++ 程式庫的第二部電腦上執行 MFC 應用程式。  
  
    1.  複製 \Release\ 資料夾的內容，然後貼到第二部電腦的應用程式資料夾中。  
  
    2.  在第二部電腦上執行應用程式。  
  
     應用程式會順利執行，因為應用程式本機資料夾中有 Visual C++ 程式庫可用。  
  
## <a name="see-also"></a>請參閱  
 [部署範例](../ide/deployment-examples.md)