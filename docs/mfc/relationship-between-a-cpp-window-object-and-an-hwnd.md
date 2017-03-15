---
title: "C++ 視窗物件和 HWND 之間的關聯性 | Microsoft Docs"
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
  - "HWND"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWnd 類別, HWND"
  - "HWND"
  - "HWND, 視窗物件"
  - "視窗物件 [C++], HWND 和"
  - "Windows 視窗 [C++]"
ms.assetid: f2e76340-6691-4ee6-9424-0345634a9469
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ 視窗物件和 HWND 之間的關聯性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

視窗 *物件* 是程式直接建立 C\+\+ `CWnd` 類別 \(或衍生類別\) 的物件。  它來來往往回應程式的建構函式和解構函式。  視窗的 *視窗*，另一方面，是不透明的控制代碼對應到視窗的內部視窗資料結構和使用系統資源，而存在。  視窗的視窗是由視窗的控制代碼」判斷 \(`HWND`\) 和建立， `CWnd` 物件藉由呼叫會建立類別的 `CWnd`**Create** 成員函式之後。  視窗會終結或已被程式呼叫或是使用者動作。  視窗控制代碼在視窗物件的 `m_hWnd` 成員變數儲存。  下圖顯示 C\+\+ 視窗物件和 Windows 視窗之間的關聯性。  建立視窗會在 [建立視窗](../mfc/creating-windows.md)中討論。  終結視窗會在 [要終結的視窗物件](../mfc/destroying-window-objects.md)中討論。  
  
 ![CWnd 視窗物件和結果視窗](../mfc/media/vc37fj1.png "vc37FJ1")  
視窗物件和 Windows 視窗  
  
## 請參閱  
 [視窗物件](../mfc/window-objects.md)