---
title: "加入 ATL 簡單物件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.classes.adding.atl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 專案, 加入物件"
  - "ATL, 簡單物件"
  - "物件 [ATL]"
ms.assetid: 9c57d2ef-0447-4c84-8982-3304b8e49847
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 加入 ATL 簡單物件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要將 ATL \(Active Template Library\) 物件加入至專案，您必須先將專案建立為 ATL 應用程式或包含 ATL 支援的 MFC 應用程式。  您可以使用 [ATL 專案精靈](../../atl/reference/atl-project-wizard.md)來建立 ATL 應用程式，或[將 ATL 支援加入至 MFC 專案](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)來為 MFC 應用程式實作 ATL 支援。  
  
 在第一次建立新的 ATL 物件時，您可為它定義 COM 介面，或是稍後從 \[類別檢視\] 捷徑功能表中，使用[實作介面](../../ide/implement-interface-wizard.md)命令來加入這些介面。  
  
### 若要將 ATL 簡單物件加入至 ATL COM 專案  
  
1.  在 \[**方案總管**\] 或[類別檢視](http://msdn.microsoft.com/zh-tw/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中，以滑鼠右鍵按一下您要加入 ATL 簡單物件的專案名稱。  
  
2.  在捷徑功能表中，按一下 \[加入\] 後再按一下 \[加入類別\]。  
  
3.  在[加入類別](../../ide/add-class-dialog-box.md)對話方塊的 \[樣板\] 窗格中，按一下 \[**ATL 簡單物件**\]，然後按一下 \[**開啟**\] 以顯示 [ATL 簡單物件精靈](../../atl/reference/atl-simple-object-wizard.md)。  
  
4.  在 ATL 簡單物件精靈的[選項](../../atl/reference/options-atl-simple-object-wizard.md)頁面上，設定專案的其他選項。  
  
5.  按一下 \[完成\] 將物件加入至專案。  
  
## 請參閱  
 [加入類別](../../ide/adding-a-class-visual-cpp.md)   
 [將新介面加入至 ATL 專案](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)   
 [Adding Connection Points to an Object](../../atl/adding-connection-points-to-an-object.md)   
 [加入方法](../../ide/adding-a-method-visual-cpp.md)   
 [MFC 類別](../../mfc/reference/adding-an-mfc-class.md)   
 [加入泛型 C\+\+ 類別](../../ide/adding-a-generic-cpp-class.md)