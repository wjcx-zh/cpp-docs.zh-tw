---
title: "Introduction to ATL Window Classes | Microsoft Docs"
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
  - "window classes"
ms.assetid: 503efc2c-a269-495d-97cf-3fb300d52f3d
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Introduction to ATL Window Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列 ATL 類別是設計來實作和管理視窗:  
  
-   [CWindow](../atl/reference/cwindow-class.md) 允許您將視窗控制代碼 `CWindow` 物件。  接著呼叫方法 `CWindow` 操作視窗。  
  
-   [CWindowImpl](../atl/reference/cwindowimpl-class.md) 可讓您實作新的視窗，並附有訊息的處理訊息對應。  您可以建立以新視窗的視窗類別， Superclass 現有類別或子類別現有視窗。  
  
-   [CDialogImpl](../atl/reference/cdialogimpl-class.md) 可讓您實作強制回應或非強制回應對話方塊並處理訊息的訊息對應。  
  
-   [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) 是實作 Windows 訊息對應到另一個類別包含預先建置的類別。  使用 `CContainedWindowT` 讓您專注於處理類別的訊息。  
  
-   [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) 可讓您實作對話方塊 \(強制回應或非強制回應\) 裝載 ActiveX 控制項。  
  
-   [CSimpleDialog](../atl/reference/csimpledialog-class.md) 可讓您實作的基本功能的強制回應對話方塊。  
  
-   [CAxWindow](../atl/reference/caxwindow-class.md) 可讓您實作裝載 ActiveX 控制項的視窗。  
  
-   [CAxWindow2T](../atl/reference/caxwindow2t-class.md) 可讓您實作裝載已授權的 ActiveX 控制項的視窗。  
  
 除了特定視窗類別之外， ATL 會提供數個類別可以實作 ATL 視窗物件更容易。  這些屬性如下：  
  
-   [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) 處理新的視窗類別的相關資訊。  
  
-   [CWinTraits](../atl/reference/cwintraits-class.md) 和 [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) 提供標準化 ATL 視窗物件特性的簡單方法。  
  
## 請參閱  
 [視窗類別](../atl/atl-window-classes.md)