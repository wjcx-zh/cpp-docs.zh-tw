---
title: "將多個檢視加入至單一文件 | Microsoft Docs"
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
  - "文件, 多重檢視"
  - "多重檢視, SDI 應用程式"
  - "單一文件介面 (SDI), 加入檢視"
  - "檢視, SDI 應用程式"
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 將多個檢視加入至單一文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在單一文件介面 \(SDI\) \(SDI\) 應用程式建立與 Microsoft Foundation Class \(MFC\) 程式庫，每個資料型別與單一檢視型別。  在某些情況下，可以交換的文件的目前檢視有新的檢視是適當的。  
  
> [!TIP]
>  如需實作多個檢視的其他程序單一文件，請參閱 [CDocument::AddView](../Topic/CDocument::AddView.md) 和 [收集](../top/visual-cpp-samples.md) MFC 範例。  
  
 您可以將新的 `CView`實作這項功能衍生類別和其他程式碼動態切換的檢視現有的 MFC 應用程式。  
  
 步驟如下：  
  
-   [修改現有的應用程式類別](#vcconmodifyexistingapplicationa1)  
  
-   [建立和修改新的檢視類別。](#vcconnewviewclassa2)  
  
-   [建立和附加新的檢視。](#vcconattachnewviewa3)  
  
-   [實作切換函式](#vcconswitchingfunctiona4)  
  
-   [加入對切換檢視](#vcconswitchingtheviewa5)  
  
 本主題的其餘部分會假設下列項目:  
  
-   `CWinApp`的名稱衍生物件為，則為 `CMyWinApp`，且 `CMyWinApp` 在 MYWINAPP.H 和 MYWINAPP.CPP 宣告和定義。  
  
-   `CNewView` 是新的 `CView`名稱衍生物件和 `CNewView` 在 NEWVIEW.H 和 NEWVIEW.CPP 宣告和定義。  
  
##  <a name="vcconmodifyexistingapplicationa1"></a> 修改現有的應用程式類別  
 對於應用程式切換檢視之間，您需要將成員變數儲存檢視和方法修改應用程式類別交換它們。  
  
 將下列程式碼加入至 `CMyWinApp` 類別，放在 MYWINAPP.H 宣告之後：  
  
 [!code-cpp[NVC_MFCDocViewSDI#1](../mfc/codesnippet/CPP/adding-multiple-views-to-a-single-document_1.h)]  
  
 新的成員變數、 `m_pOldView` 和 `m_pNewView`，指向目前檢視和新建立一個。  新的方法 \(`SwitchView`\) 切換檢視時，要求使用者。  方法的主體會在 [實作切換函式](#vcconswitchingfunctiona4)的本主題稍後會討論。  
  
 對應用程式類別的上次修改要求包括定義用來開啟或關閉函數的 Windows 訊息的新標頭檔 \(**WM\_INITIALUPDATE**\)  
  
 下行程式碼插入 MYWINAPP.CPP 的相關部分:  
  
 [!code-cpp[NVC_MFCDocViewSDI#2](../mfc/codesnippet/CPP/adding-multiple-views-to-a-single-document_2.cpp)]  
  
 儲存變更並繼續進行下一個步驟。  
  
##  <a name="vcconnewviewclassa2"></a> 建立和修改新的檢視類別。  
 建立新的檢視類別檢視可讓您輕鬆地使用 **New Class** 可用的命令。  這個類別的唯一要求是衍生自 `CView`。  將這個新的類別加入至應用程式。  如需加入新類別的特定資訊加入至專案，請參閱 [加入類別](../ide/adding-a-class-visual-cpp.md)。  
  
 一旦您將類別加入至專案，您必須變更某些檢視類別成員的存取範圍。  
  
 藉由變更存取規範修改 NEWVIEW.H 從 `protected` 加入建構函式和解構函式的 **public** 。  其為可見之前，允許類別會動態建立和終結這和修改檢視外觀。  
  
 儲存變更並繼續進行下一個步驟。  
  
##  <a name="vcconattachnewviewa3"></a> 建立和附加新的檢視。  
 若要建立和附加新的檢視，您必須修改應用程式類別的 `InitInstance` 函式。  修改將建立一個新的檢視物件。然後初始化 `m_pOldView` 和 `m_pNewView` 與現有檢視應用程式的新程式碼。  
  
 由於新的檢視在 `InitInstance` 函式中，建立新的和現有的檢視為應用程式的存留期間保存。  然而，應用程式可以輕鬆地動態建立新檢視。  
  
 在呼叫後插入下列程式碼至 `ProcessShellCommand`:  
  
 [!code-cpp[NVC_MFCDocViewSDI#3](../mfc/codesnippet/CPP/adding-multiple-views-to-a-single-document_3.cpp)]  
  
 儲存變更並繼續進行下一個步驟。  
  
##  <a name="vcconswitchingfunctiona4"></a> 實作切換函式  
 在上一個步驟中，您將建立和初始化新的檢視物件的程式碼。  最後一個主要部分是執行切換方法，則為 `SwitchView`。  
  
 在您的應用程式類別 \(MYWINAPP.CPP\) 實作檔案結尾，加入下列方法定義:  
  
 [!code-cpp[NVC_MFCDocViewSDI#4](../mfc/codesnippet/CPP/adding-multiple-views-to-a-single-document_4.cpp)]  
  
 儲存變更並繼續進行下一個步驟。  
  
##  <a name="vcconswitchingtheviewa5"></a> 加入對切換檢視  
 最後一個步驟是將呼叫 `SwitchView` 方法的程式碼，當應用程式需要切換檢視之間切換時。  這可以使用幾種方式:透過內部使用者加入新的功能表項目可選取或切換檢視，在特定條件。  
  
 如需加入新的功能表項目和命令處理常式函式的詳細資訊，請參閱 [命令和控制項通知的處理常式。](../mfc/handlers-for-commands-and-control-notifications.md)。  
  
## 請參閱  
 [文件\/檢視架構](../mfc/document-view-architecture.md)