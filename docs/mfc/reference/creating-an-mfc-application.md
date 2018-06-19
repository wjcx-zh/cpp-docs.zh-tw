---
title: 建立 MFC 應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC]
- MFC, creating applications
- MFC applications
ms.assetid: b8b8aa08-9c49-404c-8078-b42079ac18f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5b30b1e0f5e8031609845c78da7558e8b3207862
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33368809"
---
# <a name="creating-an-mfc-application"></a>建立 MFC 應用程式
MFC 應用程式以 MFC 程式庫為基礎，是 Windows 的可執行應用程式。 要建立 MFC 應用程式，最簡單的方法就是使用 MFC 應用程式精靈。  
  
> [!IMPORTANT]
>  Visual Studio Express 版本不支援 MFC 專案。  
  
 MFC 可執行檔一般分為五種類型： 標準 Windows 應用程式、 對話方塊、 表單架構應用程式、 檔案總管樣式應用程式和 Web 瀏覽器樣式應用程式。 如需詳細資訊，請參閱:  
  
-   [使用類別來撰寫 Windows 應用程式](../../mfc/using-the-classes-to-write-applications-for-windows.md)  
  
-   [建立和顯示對話方塊](../../mfc/creating-and-displaying-dialog-boxes.md)  
  
-   [建立表單架構的 MFC 應用程式](../../mfc/reference/creating-a-forms-based-mfc-application.md)  
  
-   [建立檔案總管樣式的 MFC 應用程式](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)  
  
-   [建立網頁瀏覽器樣式的 MFC 應用程式](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)  
  
 MFC 應用程式精靈可根據您在精靈中選取的選項，為任意類型的應用程式，產生適當的類別和檔案。  
  
### <a name="to-create-an-mfc-application-using-the-mfc-application-wizard"></a>若要使用 MFC 應用程式精靈建立 MFC 應用程式  
  
1.  請依照下列說明主題中的指示[使用 Visual c + + 應用程式精靈建立專案](../../ide/creating-desktop-projects-by-using-application-wizards.md)。  
  
2.  在**新專案**對話方塊中，選取**MFC 應用程式**開啟精靈的 [範本] 窗格中。  
  
3.  定義使用的應用程式設定[MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)。  
  
    > [!NOTE]
    >  若要保留精靈的預設值，請略過此步驟。  
  
4.  按一下**完成**来關閉精靈並在開發環境中開啟新專案。  
  
 您的專案建立之後，您可以檢視中建立的檔案**方案總管 中**。 如需精靈建立之專案檔案的詳細資訊，請參閱專案所產生的 ReadMe.txt 檔案。 如需檔案類型的詳細資訊，請參閱[Visual c + + 專案建立的檔案類型](../../ide/file-types-created-for-visual-cpp-projects.md)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯準備： Visual c + + Windows 應用程式](http://msdn.microsoft.com/en-us/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5)   
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [屬性頁](../../ide/property-pages-visual-cpp.md)   
 [部署應用程式](http://msdn.microsoft.com/en-us/4ff8881d-0daf-47e7-bfe7-774c625031b4)

