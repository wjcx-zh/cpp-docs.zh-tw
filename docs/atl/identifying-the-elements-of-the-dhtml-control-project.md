---
title: 識別 DHTML 控制項目元素元素
ms.date: 11/19/2018
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
ms.assetid: b627547a-3768-4346-9900-4b7a21fb8e27
ms.openlocfilehash: 5fabdc815989c21bdf6b0932b9d6826e28d7012a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319510"
---
# <a name="identifying-the-elements-of-the-dhtml-control-project"></a>識別 DHTML 控制項目元素元素

大多數 DHTML 控制代碼與為任何 ATL 控制件創建的代碼完全一樣。 要基本瞭解通用代碼,請通過[ATL 教程](../atl/active-template-library-atl-tutorial.md),並閱讀[創建 ATL 專案和 ATL](../atl/reference/creating-an-atl-project.md) [COM 物件基礎](../atl/fundamentals-of-atl-com-objects.md)部分。

DHTML 控制項類似於任何 ATL 控制項,但:

- 除了控制項實現的常規介面外,它還實現了一個用於在C++代碼和 HTML 使用者介面(UI) 之間通訊的附加介面。 使用此介面,HTML UI 調用C++代碼。

- 它為控制程式 UI 建立 HTML 資源。

- 它允許通過成員變數`m_spBrowser`訪問 DHTML 物件模型,這是[IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127\(v=vs.85\))類型的智慧指標。 使用此指標可以訪問 DHTML 物件模型的任何部分。

下圖說明了 DLL、DHTML 控制件、Web 瀏覽器和 HTML 資源之間的關係。

![DHTML 控制項專案的項目](../atl/media/vc52en1.gif "DHTML 控制項專案的項目")

> [!NOTE]
> 此圖形上的名稱是佔位符。 HTML 資源的名稱和控制項上公開的介面基於您在 ATL 控制精靈中分配它們的名稱。

在此圖形中,元素是:

- **我的 DLL**使用 ATL 專案精靈建立的 DLL。

- **DHTML**控制`m_spBrowser`件 ( ) 使用 ATL 物件精靈建立的 DHTML 控制件。 此控制者透過 Web 瀏覽器物件的介面存取 Web`IWebBrowser2`瀏覽器物件及其方法 。 除了控件所需的其他標準介面外,控件本身還公開以下兩個介面。

  - `IDHCTL1`控件公開的介面,僅供容器使用。

  - `IDHCTLUI1`用於C++代碼和 HTML 使用者介面之間通訊的調度介面。 Web 瀏覽器使用控制項的調度介面來顯示控制項。 可以通過調`window.external`用 (後)調用此調度介面上要調用的方法名稱,從控件的使用者介面調用此調度介面的各種方法。 您將從構成`window.external`此控制項的 UI 的 HTML 中的 SCRIPT 標記進行存取。 有關在資源檔中呼叫外部方法的詳細資訊,請參閱[從 DHTML 呼叫 C++代碼](../atl/calling-cpp-code-from-dhtml.md)。

- **IDR_CTL1**HTML 資源的資源識別碼。 在這種情況下,其檔名是 DHCTL1UI.htm。 DHTML 控制項使用包含標準 HTML 標記和外部視窗調度命令的 HTML 資源,您可以使用文字編輯器進行編輯。

- **網頁瀏覽器**Web 瀏覽器基於 HTML 資源中的 HTML 顯示控制項的 UI。 DHTML 控制項中提供了`IWebBrowser2`指向 Web 瀏覽器介面的指標,用於允許存取 DHTML 物件模型。

ATL 控制精靈產生一個控制項,其中包含 HTML 資源和 .cpp 檔中的預設代碼。 您可以編譯和運行精靈產生的控制項,然後在 Web 瀏覽器或 ActiveX 控制件測試容器中檢視控制件。 下圖顯示了預設的 ATL DHTML 控制項,測試容器中顯示了三個按鈕:

![ATL DHTML 控制項](../atl/media/vc52en2.gif "ATL DHTML 控制項")

請參閱[創建 ATL DHTML 控制項](../atl/creating-an-atl-dhtml-control.md)以開始建構 DHTML 控制項。 有關如何存取測試容器的資訊,請參閱[使用測試容器測試屬性和事件](../mfc/testing-properties-and-events-with-test-container.md)。

## <a name="see-also"></a>另請參閱

[DHTML 控制項的支援](../atl/atl-support-for-dhtml-controls.md)
