---
title: "ActiveX 控制項容器：在非對話方塊容器中使用控制項 | Microsoft Docs"
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
  - "ActiveX 控制項容器 [C++], 插入控制項"
  - "ActiveX 控制項容器 [C++], 非對話方塊容器"
  - "ActiveX 控制項 [C++], 建立"
  - "Create 方法 [C++], ActiveX 控制項"
  - "CreateControl 方法"
ms.assetid: 46f195b0-b8ca-4409-8cca-fbfaf2c9ab9f
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# ActiveX 控制項容器：在非對話方塊容器中使用控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在某些應用程式 \(例如 SDI 或 MDI 應用程式\)，您可以在應用程式的視窗中內嵌控制項。  包裝函式類別的 **Create** 成員函式 \(由 Visual C\+\+ 插入\)，可以動態建立控制項的執行個體，而不需對話方塊。  
  
 **Create** 成員函式具有下列參數：  
  
 `lpszWindowName`  
 對控制項中的文字或標題屬性中顯示之文字的指標 \(如果有的話\)。  
  
 `dwStyle`  
 視窗樣式。  如需完整的清單，請參閱 [CWnd::CreateControl](../Topic/CWnd::CreateControl.md)。  
  
 `rect`  
 指定控制項的大小和位置。  
  
 `pParentWnd`  
 指定控制項的父視窗，通常是 `CDialog`。  它不得為 **NULL**。  
  
 `nID`  
 指定控制項的 ID，而且可以由容器使用、參考控制項。  
  
 一個使用這函式動態建立 ActiveX 控制項的範例是在 SDI 應用程式的表單檢視。  您可以建立控制項的執行個體在應用程式的 `WM_CREATE` 處理常式中。  
  
 對於這個範例中， `CMyView` 是主要檢視類別， `CCirc` 是包裝函式類別，而 CIRC.H 是包裝函式類別的標題 \(.H\) 檔案。  
  
 實作這個功能需要四個步驟。  
  
### 若要在非對話方塊視窗動態建立 ActiveX 控制項  
  
1.  在 CMYVIEW.H 插入 CIRC.H，在 `CMyView` 類別定義之前：  
  
     [!code-cpp[NVC_MFC_AxCont#12](../mfc/codesnippet/CPP/activex-control-containers-using-controls-in-a-non-dialog-container_1.h)]  
  
2.  將成員變數 \(為 `CCirc` 型別\) 增加至位於 CMYVIEW.H 的 `CMyView` 類別定義的受保護區段：  
  
     [!code-cpp[NVC_MFC_AxCont#13](../mfc/codesnippet/CPP/activex-control-containers-using-controls-in-a-non-dialog-container_2.h)]  
    [!code-cpp[NVC_MFC_AxCont#14](../mfc/codesnippet/CPP/activex-control-containers-using-controls-in-a-non-dialog-container_3.h)]  
  
3.  若要加入訊息處理常式 `WM_CREATE` 至類別 `CMyView`。  
  
4.  在處理函式中，`CMyView::OnCreate` 呼叫控制項的 `Create` 函式 \(使用 **this** 指標做為父視窗\)：  
  
     [!code-cpp[NVC_MFC_AxCont#15](../mfc/codesnippet/CPP/activex-control-containers-using-controls-in-a-non-dialog-container_4.cpp)]  
  
5.  重建專案。  每當應用程式檢視建立時，Circ 控制項將動態建立。  
  
## 請參閱  
 [ActiveX 控制項容器](../mfc/activex-control-containers.md)