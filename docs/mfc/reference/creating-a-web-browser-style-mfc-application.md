---
title: 建立 Web 瀏覽器樣式的 MFC 應用程式
ms.date: 06/25/2018
f1_keywords:
- vc.appwiz.mfcweb.project
helpviewer_keywords:
- MFC, Web applications
- Web browsers, creating from MFC architecture
- Web browsers
- Web applications [MFC], creating
ms.assetid: 257f8c03-33c3-428c-832e-0b70aff6168d
ms.openlocfilehash: e02e928f65ab4cd918e730135abc62ed3237decf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215120"
---
# <a name="creating-a-web-browser-style-mfc-application"></a>建立 Web 瀏覽器樣式的 MFC 應用程式

網頁瀏覽器樣式的應用程式可以從網際網路（例如 HTML 或活動文檔）或內部網路，以及本機檔案系統和網路上的資料夾存取訊號。 藉由從[CHtmlView](../../mfc/reference/chtmlview-class.md)衍生應用程式的 view 類別，就能有效地將應用程式設為 Web 瀏覽器，方法是提供 WebBrowser 控制項的視圖。

## <a name="to-create-a-web-browser-application-based-on-the-mfc-documentview-architecture"></a>建立以 MFC 檔/視圖架構為基礎的 Web 瀏覽器應用程式

1. 請遵循[建立 MFC 應用程式](../../mfc/reference/creating-an-mfc-application.md)中的指示。

1. 在 [MFC 應用程式精靈] 的 [[應用程式類型](../../mfc/reference/application-type-mfc-application-wizard.md)] 頁面上，確定已選取 [**檔/視圖架構**] 方塊。 （您可以選擇 [**單一檔**] 或 [**多個檔**，但不能以**對話方塊為基礎]** ）。

1. 在 [[審查產生的類別](../../mfc/reference/generated-classes-mfc-application-wizard.md)] 頁面上，使用 [**基類**] 下拉式功能表來選取 `CHtmlView`。

1. 選取您想要內建在基本架構應用程式中的任何其他選項。

1. 按一下 [完成]。

WebBrowser 控制項支援透過超連結和統一資源定位器（URL）導覽進行網頁流覽。 控制項會維護歷程記錄清單，讓使用者可以透過先前流覽的網站、資料夾和檔來向前和向後流覽。 控制項會直接處理導覽、超連結、歷程記錄清單、我的最愛和安全性。 應用程式也可以使用 WebBrowser 控制項做為活動文檔容器，以裝載活動文檔。 因此，豐富格式的檔（例如 Microsoft Excel 試算表或 Word 檔）可以從 WebBrowser 控制項中就地開啟和編輯。 WebBrowser 控制項也是可以裝載任何 ActiveX 控制項的 ActiveX 控制項容器。

> [!NOTE]
> WebBrowser ActiveX 控制項（因此 `CHtmlView`）僅適用于在已安裝 Internet Explorer 4.0 或更新版本的 Windows 版本下執行的應用程式。

因為 `CHtmlView` 只是執行 Microsoft 網頁瀏覽器控制項，所以它的列印支援與其他[CView](../../mfc/reference/cview-class.md)衍生類別不一樣。 而是由 WebBrowser 控制項來執行印表機使用者介面和列印。 因此，`CHtmlView` 不支援「預覽列印」，而且架構不會提供其他的列印支援功能：例如， [cview：： OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)、 [CView：： OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)和[cview：： ONENDPRINTING](../../mfc/reference/cview-class.md#onendprinting)（可在其他 MFC 應用程式中取得）。

`CHtmlView` 會作為 Web 瀏覽器控制項的包裝函式，讓您的應用程式能夠看到 Web 或 HTML 網頁。 Wizard 會在 view 類別中建立[OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate)函式的覆寫，並提供 Microsoft Visual C++ Web site 的導覽連結：

```cpp
void CWebView::OnInitialUpdate()
{
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.
    Navigate2(_T("http://www.docs.microsoft.com/"),
        NULL,
        NULL);
}
```

您可以使用自己的網站來取代此網站，或者您可以使用[LoadFromResource](../../mfc/reference/chtmlview-class.md#loadfromresource)成員函式來開啟位於專案資源腳本中的 HTML 網頁，做為視圖的預設內容。 例如：

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

[MFC 範例 MFCIE](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/internet)<br/>
[MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)<br/>
[Set compiler and build properties](../../build/working-with-project-properties.md) (設定編譯器及組建屬性)<br/>
[屬性頁](../../build/reference/property-pages-visual-cpp.md)<br/>
[Set compiler and build properties](../../build/working-with-project-properties.md) (設定編譯器及組建屬性)
