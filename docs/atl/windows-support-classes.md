---
title: "Windows Support Classes | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.atl.windows"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 視窗"
  - "windows [C++], ATL"
ms.assetid: 750b14d5-d787-4d2b-9728-ac199ccad489
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Support Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列類別會提供視窗的支援:  
  
-   [\_U\_MENUorID](../atl/reference/u-menuorid-class.md) 為 **CreateWindow** 和 **CreateWindowEx**提供包裝函式。  
  
-   [CWindow](../atl/reference/cwindow-class.md) 包含作業之視窗的方法。  `CWindow` 是 `CWindowImpl`、`CDialogImpl` 和 `CContainedWindow` 的基底類別。  
  
-   [CWindowImpl](../atl/reference/cwindowimpl-class.md) 實作以新的視窗類別的一個視窗。  也可讓您存取子類別或超級類別視窗。  
  
-   [CDialogImpl](../atl/reference/cdialogimpl-class.md) 實作  對話方塊。  
  
-   [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) 實作對話方塊 \(強制回應或非強制回應\) 裝載 ActiveX 控制項。  
  
-   [CSimpleDialog](../atl/reference/csimpledialog-class.md) 實作對話方塊 \(強制回應或非強制回應\) 的基本功能。  
  
-   [CAxWindow](../atl/reference/caxwindow-class.md) 作業將 ActiveX 控制項裝載的視窗。  
  
-   [CAxWindow2T](../atl/reference/caxwindow2t-class.md) 提供管理裝載 ActiveX 控制項也支援裝載已授權的 ActiveX 控制項的視窗的方法。  
  
-   [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) 實作在另一個物件內所包含的視窗。  
  
-   [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) 處理新的視窗類別的相關資訊。  
  
-   [CDynamicChain](../atl/reference/cdynamicchain-class.md) 支援動態繫結訊息對應。  
  
-   [CMessageMap](../atl/reference/cmessagemap-class.md) 可讓物件將其訊息對應於其他物件。  
  
-   [CWinTraits](../atl/reference/cwintraits-class.md) 提供標準化 ATL 視窗物件特性的簡單方法。  
  
-   [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) 用於視窗樣式和延伸樣式提供預設值建立視窗。  使用邏輯 OR 運算子，這些值，在中，將加入至視窗的建立時所提供的值。  
  
## 相關文件  
 [ATL 視窗類別](../atl/atl-window-classes.md)  
  
 [ATL 教學課程](../atl/active-template-library-atl-tutorial.md)  
  
## 請參閱  
 [Class Overview](../atl/atl-class-overview.md)   
 [Message Map Macros](../atl/reference/message-map-macros-atl.md)   
 [Window Class Macros](../atl/reference/window-class-macros.md)