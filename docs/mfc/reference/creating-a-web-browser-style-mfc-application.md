---
title: "建立 Web 瀏覽器樣式的 MFC 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfcweb.project
dev_langs:
- C++
helpviewer_keywords:
- MFC, Web applications
- Web browsers, creating from MFC architecture
- Web browsers
- Web applications, creating
ms.assetid: 257f8c03-33c3-428c-832e-0b70aff6168d
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: ccfb093a65c3f9a72b6180c4f415a92ebaf18684
ms.lasthandoff: 02/24/2017

---
# <a name="creating-a-web-browser-style-mfc-application"></a>建立 Web 瀏覽器樣式的 MFC 應用程式
在本機檔案系統和網路上的 Web 瀏覽器樣式應用程式可以從網際網路 （例如 HTML 或主動式文件） 或內部網路，以及資料夾存取資訊。 類別衍生應用程式的檢視類別，從[CHtmlView](../../mfc/reference/chtmlview-class.md)，實際上您藉由使用 WebBrowser 控制項提供檢視使應用程式的網頁瀏覽器。  
  
### <a name="to-create-a-web-browser-application-based-on-the-mfc-documentview-architecture"></a>若要建立 MFC 文件/檢視架構為基礎的 Web 瀏覽器應用程式  
  
1.  請遵照[建立 MFC 應用程式](../../mfc/reference/creating-an-mfc-application.md)。  
  
2.  在 MFC 應用程式精靈[應用程式類型](../../mfc/reference/application-type-mfc-application-wizard.md)頁面上，請確定**文件/檢視架構**方塊。 (您可以選擇 **單一文件**或**多份文件**，但不是**對話方塊架構**。)  
  
3.  在[檢視產生的類別](../../mfc/reference/generated-classes-mfc-application-wizard.md)頁面上，使用**基底類別**下拉式選單選取`CHtmlView`。  
  
4.  選取任何其他的選項要內建基本架構應用程式。  
  
5.  按一下 [ **完成**]。  
  
 WebBrowser 控制項支援透過超連結與統一資源定位器 (URL) 瀏覽的網頁瀏覽。 控制會維護歷程記錄清單，可讓使用者瀏覽向前和向先前已瀏覽網站、 資料夾和文件。 控制項直接處理巡覽、 超連結、 歷程記錄清單、 我的最愛，以及安全性。 應用程式可以使用 WebBrowser 控制項為以及主應用程式使用中的文件的主動式文件容器。 因此，豐富格式化的文件，例如 Microsoft Excel 試算表或 Word 文件可以開啟和編輯在 WebBrowser 控制項中的位置。 WebBrowser 控制項也是可以裝載任何 ActiveX 控制項的 ActiveX 控制項容器。  
  
> [!NOTE]
>  WebBrowser ActiveX 控制項 (並因此`CHtmlView`) 只適用於 Windows 版本的 Internet Explorer 4.0 中執行的應用程式或更新版本已安裝。  
  
 因為`CHtmlView`列印方式與其他不是只會實作 Microsoft Web 瀏覽器控制項，其支援[CView](../../mfc/reference/cview-class.md)-衍生的類別。 相反地，WebBrowser 控制項實作印表機使用者介面和列印。 如此一來，`CHtmlView`並不支援列印預覽，以及架構不提供其他列印支援函式︰ 例如， [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)， [CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)，和[CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)，所提供其他 MFC 應用程式中。  
  
 `CHtmlView`做為 Web 瀏覽器控制項，可讓您的應用程式到 Web 或 HTML 網頁檢視的包裝函式。 精靈會建立覆寫， [OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate)函式在檢視類別中，提供 Microsoft Visual c + + 網站的導覽連結︰  
  
```  
void CWebView::OnInitialUpdate()  
{  
    CHtmlView::OnInitialUpdate();

 *// TODO: This code navigates to a popular spot on the web. *//  change the code to go where you'd like.  
    Navigate2(_T("http://www.msdn.microsoft.com/vstudio/"),
    NULL,
    NULL);

} 
```  
  
 您可以將此站台取代為您自己，或者您可以使用[LoadFromResource](../../mfc/reference/chtmlview-class.md#loadfromresource)成員函式來開啟 HTML 網頁位於專案的資源指令碼，做為檢視的預設內容。 例如:   
  
```  
void CWebView::OnInitialUpdate()  
{  
    CHtmlView::OnInitialUpdate();

 *// TODO: This code navigates to a popular spot on the web. *//  change the code to go where you'd like.  
    LoadFromResource(IDR_HTML1);

} 
```  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 MFCIE](http://msdn.microsoft.com/en-us/7391aa0c-fca8-4994-a6c9-6c5c7470fba0)   
 [MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)   
 [使用專案屬性](../../ide/working-with-project-properties.md)   
 [屬性頁](../../ide/property-pages-visual-cpp.md)   
 [使用專案屬性](../../ide/working-with-project-properties.md)   
 [部署應用程式](http://msdn.microsoft.com/en-us/4ff8881d-0daf-47e7-bfe7-774c625031b4)


