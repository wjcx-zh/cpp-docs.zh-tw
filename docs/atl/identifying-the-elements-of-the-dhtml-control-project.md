---
title: 識別 DHTML 控制項專案的項目 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
ms.assetid: b627547a-3768-4346-9900-4b7a21fb8e27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 868feab383c324962c05fc5e341092cf89f895f5
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752829"
---
# <a name="identifying-the-elements-of-the-dhtml-control-project"></a>識別 DHTML 控制項專案的項目

大部分的 DHTML 控制項程式碼完全像這樣會建立任何 ATL 的控制項。 泛型的程式碼的基本了解，逐步[ATL 教學課程](../atl/active-template-library-atl-tutorial.md)，並參閱的章節[建立 ATL 專案](../atl/reference/creating-an-atl-project.md)並[ATL COM 物件的基本概念](../atl/fundamentals-of-atl-com-objects.md)。

DHTML 控制項是類似於任何 ATL 的控制項，除了：

- 除了一般的介面的控制項實作，它會實作使用 c + + 程式碼和 HTML 使用者介面 (UI) 之間進行通訊的其他介面。 HTML UI 呼叫 c + + 程式碼使用此介面。

- 它會建立 UI 控制項的 HTML 資源。

- 它可讓 DHTML 物件模型，透過成員變數的存取權`m_spBrowser`，這是類型的智慧型指標[IWebBrowser2](https://msdn.microsoft.com/library/aa752127.aspx)。 您可以使用這個指標來存取 DHTML 物件模型的任何部分。

下圖說明您的 DLL、 DHTML 控制項、 網頁瀏覽器和 HTML 資源之間的關聯性。

![DHTML 控制項專案的項目](../atl/media/vc52en1.gif "vc52en1")

> [!NOTE]
>  此圖形上的名稱是預留位置。 ATL 控制項精靈中所指派的名稱會以 HTML 資源和控制項上所公開的介面的名稱。

在此圖中的元素如下：

- **我的 DLL**使用 ATL 專案精靈 建立的 DLL。

- **DHTML 控制項**(`m_spBrowser`) DHTML 控制項，使用 [ATL 物件精靈] 建立。 這個控制項透過 Web 瀏覽器物件的介面，存取 Web 瀏覽器物件和其方法`IWebBrowser2`。 控制項本身會公開下列兩個介面，除了其他控制所需的標準介面。

   - `IDHCTL1` 僅供容器使用的控制項所公開的介面。

   - `IDHCTLUI1` C + + 程式碼和 HTML 使用者介面之間的通訊分派介面。 網頁瀏覽器會使用控制項的分派介面，來顯示控制項。 您可以從控制項的使用者介面呼叫此分派介面的各種方法，藉由叫用`window.external`，後面接著在您想要叫用這個分派介面上的方法名稱。 您可存取`window.external`從指令碼標記的 HTML，組成此控制項的 UI 中。 如需有關如何叫用的資源檔中的外部方法的詳細資訊，請參閱[從 DHTML 呼叫 c + + 程式碼](../atl/calling-cpp-code-from-dhtml.md)。

- **IDR_CTL1** HTML 資源的資源識別碼。 其檔案名稱，在此情況下，是 DHCTL1UI.htm。 DHTML 控制項使用的是包含標準的 HTML 標記和外部視窗分派命令，您可以使用文字編輯器來編輯的 HTML 資源。

- **Web 瀏覽器**Web 瀏覽器會顯示控制項的 UI 中，根據 HTML 資源中的 HTML。 網頁瀏覽器的指標`IWebBrowser2`介面可供使用 DHTML 控制項，以允許存取 DHTML 物件模型中。

ATL 控制項精靈會產生具有預設的程式碼的控制項的 HTML 資源和.cpp 檔案中。 您可以編譯和執行精靈時，所產生的控制項，然後在網頁瀏覽器或 ActiveX 控制項測試容器中檢視控制項。 下圖顯示含有三個按鈕顯示在測試容器中的 ATL DHTML 控制項的預設值：

![ATL DHTML 控制項](../atl/media/vc52en2.gif "vc52en2")

請參閱[建立 ATL DHTML 控制項](../atl/creating-an-atl-dhtml-control.md)開始建立 DHTML 控制項。 請參閱[以測試容器測試屬性和事件](../mfc/testing-properties-and-events-with-test-container.md)如需有關如何測試容器存取資訊。

## <a name="see-also"></a>另請參閱

[DHTML 控制項的支援](../atl/atl-support-for-dhtml-controls.md)

