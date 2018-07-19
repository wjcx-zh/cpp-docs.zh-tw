---
title: 建立 Web 瀏覽器樣式的 MFC 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfcweb.project
dev_langs:
- C++
helpviewer_keywords:
- MFC, Web applications
- Web browsers, creating from MFC architecture
- Web browsers
- Web applications [MFC], creating
ms.assetid: 257f8c03-33c3-428c-832e-0b70aff6168d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2a3b0e148104ff5620eddf7ac0d26693d96607d9
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/13/2018
ms.locfileid: "39025652"
---
# <a name="creating-a-web-browser-style-mfc-application"></a>建立 Web 瀏覽器樣式的 MFC 應用程式
在本機檔案系統和網路上的 Web 瀏覽器型應用程式可以從網際網路 （例如 HTML 或主動式文件） 或內部網路，以及資料夾存取資訊。 藉由從應用程式的檢視類別的衍生[CHtmlView](../../mfc/reference/chtmlview-class.md)，以有效地您所提供的檢視，和 WebBrowser 控制項讓應用程式的網頁瀏覽器。  
  
### <a name="to-create-a-web-browser-application-based-on-the-mfc-documentview-architecture"></a>若要建立 MFC 文件/檢視架構為基礎的 Web 瀏覽器應用程式  
  
1.  請遵照[建立 MFC 應用程式](../../mfc/reference/creating-an-mfc-application.md)。  
  
2.  在 MFC 應用程式精靈[應用程式類型](../../mfc/reference/application-type-mfc-application-wizard.md)頁面上，請確定**文件/檢視架構**選取方塊。 (您可以選擇**單一文件**或是**多份文件**，而非**採用對話方塊**。)  
  
3.  在上[檢閱產生的類別](../../mfc/reference/generated-classes-mfc-application-wizard.md)頁面上，使用**基底類別**下拉式功能表來選取`CHtmlView`。  
  
4.  選取任何其他的選項您想要建置在基本架構的應用程式。  
  
5.  按一下 [ **完成**]。  
  
 WebBrowser 控制項支援透過超連結和統一資源定位器 (URL) 瀏覽的網頁瀏覽。 控制項有一份歷程記錄，可讓使用者瀏覽向前和回溯到先前已瀏覽網站、 資料夾和文件。 這個控制項直接負責瀏覽、 超連結、 歷程記錄清單、 我的最愛，以及安全性。 應用程式可以做的主動式文件容器，以及裝載作用中的文件以使用 WebBrowser 控制項。 因此，豐富格式化的文件，例如 Microsoft Excel 試算表或 Word 文件可以開啟和編輯從 WebBrowser 控制項內的位置。 WebBrowser 控制項也是一個可以裝載任何 ActiveX 控制項的 ActiveX 控制項容器。  
  
> [!NOTE]
>  WebBrowser ActiveX 控制項 (並因此`CHtmlView`) 只適用於 Internet Explorer 4.0 中的 Windows 版本下執行的應用程式或更新版本已安裝。  
  
 因為`CHtmlView`只會實作 Microsoft Web 瀏覽器控制項，其支援，列印不像其他[CView](../../mfc/reference/cview-class.md)-衍生的類別。 相反地，WebBrowser 控制項所實作的印表機使用者介面和列印。 如此一來，`CHtmlView`並不支援列印預覽狀態，以及架構不提供其他列印支援函式： 例如， [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)， [CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)，並[CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)，所提供的其他 MFC 應用程式。  
  
 `CHtmlView` 做為 Web 瀏覽器控制項，可讓您的應用程式到 Web 或 HTML 網頁檢視的包裝函式。 此精靈會建立覆寫[OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate)檢視類別，提供 Microsoft Visual c + + 網站的導覽連結中的函式：  
  
```cpp
void CWebView::OnInitialUpdate()  
{  
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.  
    Navigate2(_T("http://www.msdn.microsoft.com/vstudio/"),
        NULL,
        NULL);
}
```

您可以使用您自己，取代此站台，或者您可以使用[LoadFromResource](../../mfc/reference/chtmlview-class.md#loadfromresource)成員函式來開啟 HTML 網頁位於專案的資源指令碼，做為預設內容檢視。 例如:   
  
```cpp
void CWebView::OnInitialUpdate()  
{  
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.  
    LoadFromResource(IDR_HTML1);
}
```  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 MFCIE](http://msdn.microsoft.com/7391aa0c-fca8-4994-a6c9-6c5c7470fba0)   
 [MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)   
 [使用專案屬性](../../ide/working-with-project-properties.md)   
 [屬性頁](../../ide/property-pages-visual-cpp.md)   
 [使用專案屬性](../../ide/working-with-project-properties.md)   
 [部署應用程式](http://msdn.microsoft.com/4ff8881d-0daf-47e7-bfe7-774c625031b4)

