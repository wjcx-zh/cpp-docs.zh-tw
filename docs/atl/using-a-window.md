---
title: "Using a Window | Microsoft Docs"
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
  - "ATL, 視窗"
  - "CWindow class, about CWindow class"
  - "windows [C++], ATL"
ms.assetid: b3b9cc8e-4287-486b-b080-38852bc2943a
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Using a Window
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

類別 [CWindow](../atl/reference/cwindow-class.md) 可讓您使用  視窗。  一旦您將視窗為 `CWindow` 物件，您就可以呼叫方法 `CWindow` 操作視窗。  `CWindow` 也包含一 `HWND` 運算子轉換成 `HWND`的 `CWindow` 物件。  如此您便可傳遞至要求視窗的控制代碼之函式的一 `CWindow` 物件。  您可以輕易地混合 `CWindow` 方法呼叫和 Win32 函式呼叫，則不會建立任何暫存物件。  
  
 由於 `CWindow` 只有兩個資料成員 \(Windows 控制代碼和預設大小 \(\)，則不會受到額外負荷給與您的程式碼。  此外，許多 `CWindow` 方法包裝對應的 Win32 API 函式。  您可以使用 `CWindow`， `HWND` 成員會自動傳遞至 Win32 函式。  
  
 除了直接使用 `CWindow` 之外，您也可以從它衍生資料或將程式碼加入至類別。  ATL `CWindow`從取得三個類別: [CWindowImpl](../atl/implementing-a-window.md)、 [CDialogImpl](../atl/implementing-a-dialog-box.md)和 [CContainedWindowT](../atl/using-contained-windows.md)。  
  
## 請參閱  
 [視窗類別](../atl/atl-window-classes.md)