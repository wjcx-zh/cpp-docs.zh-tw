---
title: "DHTML 控制項專案的項目用來識別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
ms.assetid: b627547a-3768-4346-9900-4b7a21fb8e27
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 74b271f56fe7c8d3345ce53de06a18a2700175f2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="identifying-the-elements-of-the-dhtml-control-project"></a>識別 DHTML 控制項專案的項目
大部分 DHTML 控制項的程式碼完全像那樣建立任何 ATL 的控制項。 泛型程式碼的基本了解，逐步[ATL 教學課程](../atl/active-template-library-atl-tutorial.md)，並參閱的章節[ATL 專案建立](../atl/reference/creating-an-atl-project.md)和[ATL COM 物件基礎觀念](../atl/fundamentals-of-atl-com-objects.md)。  
  
 DHTML 控制項是類似於任何 ATL 的控制項，除了：  
  
-   除了一般的介面控制項實作，它會實作其他介面，用於 c + + 程式碼和 HTML 的使用者介面 (UI) 之間進行通訊。 HTML UI 呼叫 c + + 程式碼使用此介面。  
  
-   它會建立 UI 控制項的 HTML 資源。  
  
-   它可讓您存取 DHTML 物件模型，透過成員變數`m_spBrowser`，這是類型的智慧型指標[IWebBrowser2](https://msdn.microsoft.com/library/aa752127.aspx)。 您可以使用這個指標來存取 DHTML 物件模型的任何部分。  
  
 下圖說明您的 DLL、 DHTML 控制項、 網頁瀏覽器和 HTML 資源之間的關聯性。  
  
 ![DHTML 控制項專案的項目](../atl/media/vc52en1.gif "vc52en1")  
  
> [!NOTE]
>  此圖形上的名稱為預留位置。 HTML 資源的控制項上所公開的介面名稱根據 ATL 控制項精靈中所指派的名稱。  
  
 此圖中的元素為：  
  
-   **我的 DLL**使用 ATL 專案精靈所建立的 DLL。  
  
-   **DHTML 控制項**(`m_spBrowser`) DHTML 控制項，使用 ATL 物件精靈所建立。 這個控制項可透過網頁瀏覽器物件的介面存取網頁瀏覽器物件和其方法**IWebBrowser2**。 在控制項本身會公開下列兩個介面上，除了控制所需的其他標準介面。  
  
    -   **IDHCTL1**僅可供容器使用的控制項所公開的介面。  
  
    -   **IDHCTLUI1**分派介面的 c + + 程式碼與 HTML 使用者介面之間進行通訊。 網頁瀏覽器會顯示控制項使用的控制項分派介面。 您可以從控制項的使用者介面呼叫此分派介面的各種方法，藉由叫用`window.external`，後面接著您要叫用此分派介面上的方法名稱。 會存取`window.external`從指令碼內所組成的 UI，對這個控制項的 HTML 標記。 如需叫用的資源檔中的外部方法的詳細資訊，請參閱[呼叫 c + + 程式碼從 DHTML](../atl/calling-cpp-code-from-dhtml.md)。  
  
-   **IDR_CTL1** HTML 資源的資源識別碼。 其檔案名稱，在此情況下，是 DHCTL1UI.htm。 DHTML 控制項，會使用包含標準的 HTML 標記和外部視窗分派命令，您可以使用文字編輯器來編輯 HTML 資源。  
  
-   **Web 瀏覽器**Web 瀏覽器會顯示控制項的 UI 中，根據 HTML 資源中的 HTML。 網頁瀏覽器的指標**IWebBrowser2**介面是可在 DHTML 控制項，以允許存取 DHTML 物件模型。  
  
 ATL 控制項精靈產生 HTML 資源和.cpp 檔案中的預設程式碼的控制項。 您可以編譯和執行精靈所產生的控制項，然後檢視在網頁瀏覽器或 ActiveX 控制項測試容器中的控制項。 下圖顯示測試容器中的三個按鈕顯示 ATL DHTML 控制項的預設值：  
  
 ![ATL DHTML 控制項](../atl/media/vc52en2.gif "vc52en2")  
  
 請參閱[建立 ATL DHTML 控制項](../atl/creating-an-atl-dhtml-control.md)若要開始在建立 DHTML 控制項。 請參閱[使用測試容器測試屬性和事件](../mfc/testing-properties-and-events-with-test-container.md)如何存取測試容器的資訊。  
  
## <a name="see-also"></a>請參閱  
 [DHTML 控制項的支援](../atl/atl-support-for-dhtml-controls.md)

