---
title: "Identifying the Elements of the DHTML Control Project | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DHTML controls, ATL 支援"
  - "HTML 控制項, ATL 支援"
ms.assetid: b627547a-3768-4346-9900-4b7a21fb8e27
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Identifying the Elements of the DHTML Control Project
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

大部分的 DHTML 控制代碼是完全一樣的所有 ATL 控制項建立的相同。  如需泛型程式碼，工作的基本了解透過 [ATL 教學課程](../atl/active-template-library-atl-tutorial.md)和讀取部分 [建立 ATL 專案](../atl/reference/creating-an-atl-project.md) 和 [ATL COM 物件的基本概念](../atl/fundamentals-of-atl-com-objects.md)。  
  
 DHTML 控制項類似於所有 ATL 控制項，除了:  
  
-   除了這個規則外連接控制項實作，該實作來通訊在 C\+\+ 程式碼和 HTML 使用者介面 \(UI\) 之間的其他介面。  HTML 使用者介面的呼叫中使用這個介面的 C\+\+ 程式碼。  
  
-   它會建立一個 HTML 控制項的 UI 資源。  
  
-   它會透過成員變數 `m_spBrowser`允許存取 DHTML 物件模型的存取，這個型別 [IWebBrowser2](https://msdn.microsoft.com/en-us/library/aa752127.aspx)的智慧型指標。  使用此指標來存取 DHTML 物件模型的任何部分。  
  
 下圖顯示您的 DLL、DHTML 控制項、Web 瀏覽器和 HTML 資源之間的關聯性。  
  
 ![DHTML 控制項專案的項目](../atl/media/vc52en1.png "vc52EN1")  
  
> [!NOTE]
>  在圖形中的名稱是替代符號 \(Placeholder\)。  在您的控制項公開的 HTML 資源和介面的名稱會根據您在 ATL 控制項精靈指派其名稱。  
  
 在圖形中，項目是:  
  
-   **My DLL** 使用 ATL 專案精靈建立的 DLL。  
  
-   **DHTML Control** \(\)`m_spBrowser`DHTML 控制項，建立使用 ATL 物件精靈。  這個控制項透過 Web 瀏覽器物件的介面， **IWebBrowser2**存取 Web 瀏覽器物件和它的方法。  控制項會公開 \(Expose\) 下列兩個介面，除了針對控制項所需的其他標準介面之外。  
  
    -   **IDHCTL1** 控制項所公開的介面只能由容器。  
  
    -   **IDHCTLUI1** 通訊的分派介面在 C\+\+ 程式碼和 HTML 使用者介面之間。  Web 瀏覽器使用控制項的分派介面顯示控制項。  您可以叫用 \(Invoke\) 呼叫這個 `window.external`分派介面的各種方法從控制項的使用者介面中，接著在此分派介面上的方法名稱與要叫用。  您從組成這個控制項的 UI 在 HTML 中的指令碼標記會存取 `window.external` 。  如需叫用在資源檔中的外部方法的詳細資訊，請參閱 [呼叫來自 DHTML 的 C\+\+ 程式碼](../atl/calling-cpp-code-from-dhtml.md)。  
  
-   **IDR\_CTL1** HTML 資源的資源 ID。  它的檔名，在這個案例中，是 DH CTL1 UI.htm。  DHTML 控制項使用文字編輯器，其中包含標準 HTML 標記，而外部視窗分派命令的 HTML 資源可以編輯。  
  
-   **Web Browser** Web 瀏覽器以 HTML 在 HTML 表格中顯示控制項的 UI。  至 Web 瀏覽器的 **IWebBrowser2** 介面指標。可用於 DHTML 控制項允許存取 DHTML 物件模型的存取。  
  
 ATL 控制項精靈產生程式碼的預設控制項會顯示 HTML 資源和 .cpp 檔案。  您可以編譯和執行產生的控制項是由精靈，然後檢視 \[Web 瀏覽器或 ActiveX 控制項測試容器的控制項。  下面的圖片在測試容器顯示具有三個按鈕的預設 ATL DHTML 控制項:  
  
 ![ATL DHTML 控制項](../atl/media/vc52en2.png "vc52EN2")  
  
 請參閱 [建立 ATL DHTML 控制項](../atl/creating-an-atl-dhtml-control.md) 開始建立 DHTML 控制項。  如需如何存取測試容器的詳細資訊，請參閱 [測試屬性和事件會和測試容器](../mfc/testing-properties-and-events-with-test-container.md) 。  
  
## 請參閱  
 [DHTML 控制項的支援](../atl/atl-support-for-dhtml-controls.md)