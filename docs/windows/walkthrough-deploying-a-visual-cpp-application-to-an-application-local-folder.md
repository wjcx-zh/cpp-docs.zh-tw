---
title: 將 Visual C++ 應用程式部署至應用程式本機資料夾
ms.date: 09/17/2018
helpviewer_keywords:
- deploying Visual C++ applications
ms.assetid: 47a81c47-9dbe-47c6-96cc-fbb2fda5e6ad
ms.openlocfilehash: 33edf4bb736fad62928e11dd0550af6640d411ac
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58786171"
---
# <a name="walkthrough-deploying-a-visual-c-application-to-an-application-local-folder"></a>逐步解說：將 Visual C++ 應用程式部署到應用程式本機資料夾

描述如何透過將檔案複製到其資料夾來部署 Visual C++ 應用程式。

## <a name="prerequisites"></a>必要條件

- 已安裝 Visual Studio 的電腦。

- 沒有 Visual C++ 程式庫的另一部電腦。

### <a name="to-deploy-an-application-to-an-application-local-folder"></a>將應用程式部署至應用程式本機資料夾

1. 藉由遵循[逐步解說：使用安裝專案部署 Visual C++ 應用程式](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)中的步驟來建立及建置 MFC 應用程式：。

1. 從 \\VC\\redist\\*version* 資料夾中的 Visual Studio 安裝目錄，複製適當的 MFC 和 C 執行階段 (CRT) 程式庫檔案，然後將其貼上於 MFC 專案的 \Release\ 資料夾中。 如需您可能必須複製之其他檔案的詳細資訊，請參閱[決定要轉散發哪些 DLL](determining-which-dlls-to-redistribute.md)。

1. 在沒有 Visual C++ 程式庫的第二部電腦上執行 MFC 應用程式。

   1. 複製 \Release\ 資料夾的內容，然後貼到第二部電腦的應用程式資料夾中。

   1. 在第二部電腦上執行應用程式。

   應用程式會順利執行，因為應用程式本機資料夾中有 Visual C++ 程式庫可用。

## <a name="see-also"></a>另請參閱

[部署範例](deployment-examples.md)<br/>
