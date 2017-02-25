---
title: "建立 Web 瀏覽器樣式的 MFC 應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfcweb.project"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC, Web 應用程式"
  - "Web 應用程式, 建立"
  - "Web 瀏覽器"
  - "Web 瀏覽器, 從 MFC 架構建立"
ms.assetid: 257f8c03-33c3-428c-832e-0b70aff6168d
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 建立 Web 瀏覽器樣式的 MFC 應用程式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Web 瀏覽器樣式的應用程式可以從網際網路 \(例如 HTML 或主動式文件\) 或內部網路存取資訊，也可以在本機檔案系統及網路上存取資料夾。  藉由從 [CHtmlView](../../mfc/reference/chtmlview-class.md) 衍生應用程式的檢視類別，您可經由提供包含 WebBrowser 控制項的檢視，有效的讓應用程式成為 Web 瀏覽器。  
  
### 若要根據 MFC 文件\/檢視架構，建立 Web 瀏覽器應用程式  
  
1.  請依照[建立 MFC 應用程式](../../mfc/reference/creating-an-mfc-application.md)的指示進行操作。  
  
2.  在 MFC 應用程式精靈的[應用程式類型](../../mfc/reference/application-type-mfc-application-wizard.md)頁面中，確認是否已核取 \[支援文件\/檢視架構\] 方塊 \(您可以選擇 \[單一文件\] 或 \[多重文件\]，但不可以選擇 \[以對話方塊為基礎\]\)。  
  
3.  在[檢視產生的類別](../../mfc/reference/generated-classes-mfc-application-wizard.md)頁面上，使用 \[基底類別\] 下拉式功能表選取 \[`CHtmlView`\]。  
  
4.  請選取您要在基本架構應用程式上建立的其他選項。  
  
5.  按一下 \[**完成**\]。  
  
 WebBrowser 控制項可透過超連結 \(Hyperlink\) 和統一資源定位器 \(URL\) 巡覽，支援 Web 瀏覽。  控制項可維護歷程記錄清單，以允許使用者前進或倒退瀏覽之前瀏覽過的網站、資料夾和文件。  控制項直接處理巡覽、超連結、歷程記錄清單、我的最愛和安全性。  應用程式可使用 WebBrowser 控制項做為主動式文件容器，以同時裝載現用文件。  因此，如 Microsoft Excel 試算表或 Word 文件等完全格式化文件，皆可於 WebBrowser 控制項內開啟和編輯。  WebBrowser 控制項也就是能夠裝載任意 ActiveX 控制項的 ActiveX 控制項容器。  
  
> [!NOTE]
>  WebBrowser ActiveX 控制項 \(也就是 `CHtmlView`\) 僅適用於 Windows 版本下 \(其中安裝有 Internet Explorer 4.0 或更新版本\) 執行的應用程式。  
  
 由於 `CHtmlView` 僅實作 Microsoft Web 瀏覽器控制項，對於列印方面的支援並不如其他 [CView](../../mfc/reference/cview-class.md) 衍生的類別。  相反地，WebBrowser 控制項可實行印表機使用者介面和列印作業。  因此，`CHtmlView` 不支援預覽列印，而且不為其他列印支援功能提供架構：例如，[CView::OnPreparePrinting](../Topic/CView::OnPreparePrinting.md)、[CView::OnBeginPrinting](../Topic/CView::OnBeginPrinting.md) 以及 [CView::OnEndPrinting](../Topic/CView::OnEndPrinting.md)，這些在其他 MFC 應用程式中皆可適用。  
  
 `CHtmlView` 像是 Web 瀏覽器控制項的包裝函式，提供應用程式對 Web 或 HTML 網頁的檢視。  精靈會在檢視類別中，建立 [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md) 函式的覆寫函式，提供連至 Microsoft Visual C\+\+ 網站的巡覽式連結：  
  
```  
void CWebView::OnInitialUpdate()  
{  
   CHtmlView::OnInitialUpdate();  
  
   // TODO: This code navigates to a popular spot on the web.  
   //  change the code to go where you'd like.  
   Navigate2(_T("http://www.msdn.microsoft.com/vstudio/"),NULL,NULL);  
}  
```  
  
 您可以使用個人網站來取代此網站，或者也可以使用 [LoadFromResource](../Topic/CHtmlView::LoadFromResource.md) 成員 \(Member\) 函式來開啟位於專案的資源指令碼的 HTML 網頁，做為預設檢視內容。  例如：  
  
```  
void CWebView::OnInitialUpdate()  
{  
   CHtmlView::OnInitialUpdate();  
  
   // TODO: This code navigates to a popular spot on the web.  
   //  change the code to go where you'd like.  
   LoadFromResource(IDR_HTML1);  
}  
```  
  
## 請參閱  
 [MFC Sample MFCIE](http://msdn.microsoft.com/zh-tw/7391aa0c-fca8-4994-a6c9-6c5c7470fba0)   
 [MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)   
 [使用專案屬性](../../ide/working-with-project-properties.md)   
 [屬性頁](../../ide/property-pages-visual-cpp.md)   
 [使用專案屬性](../../ide/working-with-project-properties.md)   
 [Deploying Applications](http://msdn.microsoft.com/zh-tw/4ff8881d-0daf-47e7-bfe7-774c625031b4)