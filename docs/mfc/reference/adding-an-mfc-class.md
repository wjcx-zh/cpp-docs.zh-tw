---
title: "加入 MFC 類別 | Microsoft Docs"
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
  - "vc.codewiz.classes.adding.mfc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "類別 [C++], 加入 MFC"
  - "MFC, 加入類別"
ms.assetid: 9a96b67f-40bf-43d4-8872-2f8dfc5404f1
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 加入 MFC 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要將衍生自 MFC 程式庫類別的類別加入至專案，請使用[類別檢視](http://msdn.microsoft.com/zh-tw/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中可用的 \[加入類別\] 命令。  指定新類別的名稱、選取基底類別並選取關聯的對話方塊 ID \(如果有\)。  程式碼精靈會建立標頭檔 \(Header File\) 和實作檔並將它們加入至您的專案。  
  
> [!NOTE]
>  如果您最初[建立具有 MFC 支援的應用程式](../../atl/reference/mfc-support-in-atl-projects.md)，則可以將 MFC 類別加入至 ATL COM 應用程式。  您也可以將 MFC 類別加入至具有 MFC 支援的 Win32 專案。  
  
### 若要將 MFC 類別加入至您的專案  
  
1.  在 \[類別檢視\] 中以滑鼠右鍵按一下專案名稱。  按一下 \[加入\]，然後按一下 \[加入類別\] 開啟[加入類別](../../ide/add-class-dialog-box.md)對話方塊。  
  
2.  在 \[範本\] 清單中選取 \[**MFC 類別**\]，然後按 \[**加入**\] 按鈕。  
  
3.  在 [MFC 類別精靈](../../mfc/reference/mfc-add-class-wizard.md)對話方塊中定義新類別的設定。  
  
4.  按一下 \[完成\] 以關閉精靈，並在 \[類別檢視\] 中檢視新類別。  您也可以在**方案總管**中檢視精靈建立的檔案。  
  
## 請參閱  
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [加入類別](../../ide/adding-a-class-visual-cpp.md)   
 [類別概觀](../../mfc/class-library-overview.md)