---
title: "Modifying the ATL DHTML Control | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DHTML controls"
  - "DHTML controls, 修改"
  - "HTML 控制項, 修改"
ms.assetid: c053f35f-8629-4600-9595-721f5956777a
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Modifying the ATL DHTML Control
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL 控制項精靈提供起始程式碼，讓您可以建立和執行控制項，和，以便您可以查看方法如何在專案檔，以及如何 DHTML 呼叫使用 Dispatch 方法之控制項的 C\+\+ 程式碼。  您可以將所有的方法僅將事件分派至介面。  然後，您可以在 HTML 資源可以呼叫方法。  
  
#### 修改 ATL DHTML 控制項  
  
1.  在 \[類別檢視\] 中，展開控制項專案。  
  
     請注意在 UI」結尾有方法， `OnClick`的介面。  在「UI」未關閉的介面並沒有任何方法。  
  
2.  將名為 `MethodInvoked`的方法加入至 UI 不結束介面」。  
  
     這個方法會加入至用來控制項容器的容器互動的介面，而不適用於 DHTML 用來介面與控制項互動。  只有容器可以叫用這個方法。  
  
3.  例如尋找在 .cpp 檔的截短的方法並加入程式碼來顯示訊息方塊，:  
  
     [!code-cpp[NVC_ATL_COM#5](../atl/codesnippet/CPP/modifying-the-atl-dhtml-control_1.cpp)]  
  
4.  將名為 `HelloHTML`的另一個方法，在中，只有這次，將它加入至介面中的「UI 的結尾」。例如尋找在 .cpp 檔的截短的 `HelloHTML` 方法並加入程式碼來顯示訊息方塊，:  
  
     [!code-cpp[NVC_ATL_COM#6](../atl/codesnippet/CPP/modifying-the-atl-dhtml-control_2.cpp)]  
  
5.  將第三個方法， `GoToURL`，至 UI 不結束介面」。藉由呼叫 [IWebBrowser2::Navigate](https://msdn.microsoft.com/en-us/library/aa752133.aspx)實作此方法，如下所示:  
  
     [!code-cpp[NVC_ATL_COM#7](../atl/codesnippet/CPP/modifying-the-atl-dhtml-control_3.cpp)]  
  
     因為 ATL 提供指標至該介面為您的 .h 檔案，您可以使用 **IWebBrowser2** 方法。  
  
 接著，請修改 HTML 資源叫用您所建立的方法。  您會將叫用這些方法的三個按鈕。  
  
#### 修改 HTML 資源  
  
1.  在 \[方案總管\] 中，按兩下 .htm 檔顯示 HTML 資源。  
  
     檢查 HTML，對外部視窗 \(特別是方法的呼叫。  HTML 呼叫專案 `OnClick` 方法，，和參數表示控制項 \(`theBody`\) 和色彩的主體`red`指派 \(" "\)。  在方法呼叫後的文字是顯示在按鈕的標籤。  
  
2.  將另一個方法， `OnClick` ，只有變更色彩。  例如：  
  
    ```  
    <br>  
    <br>  
    <BUTTON onclick='window.external.OnClick(theBody, "white");'>Refresh</BUTTON>  
    ```  
  
     這個方法會建立按鈕，標記 **重新整理**，使用者可以按一下  將控制項傳回到原始，白色背景。  
  
3.  將呼叫加入至您所建立的 `HelloHTML` 方法。  例如：  
  
    ```  
    <br>  
    <br>  
    <BUTTON onclick='window.external.HelloHTML();'>HelloHTML</BUTTON>  
    ```  
  
     這個方法會建立按鈕，標記 **HelloHTML**，使用者可以按一下  以顯示 `HelloHTML` 訊息方塊。  
  
 您現在可以建置並 [測試已修改的 DHTML 控制項](../atl/testing-the-modified-atl-dhtml-control.md)。  
  
## 請參閱  
 [DHTML 控制項的支援](../atl/atl-support-for-dhtml-controls.md)