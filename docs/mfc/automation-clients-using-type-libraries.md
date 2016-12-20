---
title: "Automation 用戶端：使用類型程式庫 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MkTypLib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".odl 檔案"
  - "Automation 用戶端, 類型程式庫"
  - "類別 [C++], 分派"
  - "用戶端, Automation"
  - "分派類別"
  - "MkTypLib 工具"
  - "ODL (物件描述語言)"
  - "ODL 檔案"
  - "類型程式庫, Automation 用戶端"
ms.assetid: d405bc47-118d-4786-b371-920d035b2047
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Automation 用戶端：使用類型程式庫
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果用戶端要管理伺服器的物件， Automation 用戶端必須對伺服器物件的屬性和方法的相關資訊。  屬性有資料型別;通常方法傳回值和接受參數。  用戶端要求有關的任何資料型別的資訊這些以靜態方式繫結至伺服器物件型別。  
  
 型別資訊可傳達使用數種方式。  這個建議的方式是建立型別程式庫。  
  
 如需 [MkTypLib](http://msdn.microsoft.com/library/windows/desktop/aa366797)的詳細資訊，請參閱 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]。  
  
 Visual C\+\+ 無法讀取型別程式庫檔案並建立衍生自 [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)的分派類別。  該類別的物件有重複這些伺服器物件的屬性和作業。  您的應用程式呼叫此物件的屬性和作業，因此，從 `COleDispatchDriver` 繼承的功能傳送這些呼叫 OLE 系統，則會傳送至伺服器物件。  
  
 Visual C\+\+ 會自動維護您的這個型別程式庫檔案，如果您選擇包含 Automation，當建立專案。  為每個組建的一部分，則 .tlb 檔將會用 MkTypLib 將建立。  
  
### 建立分派類別從型別程式庫 \(.tlb\) 檔案  
  
1.  在類別檢視或方案總管中，以滑鼠右鍵按一下 **Add** 和 **Add Class** 按一下捷徑功能表。  
  
2.  在 **Add Class** 對話方塊中，選取左窗格的 **Visual C\+\+\/MFC** 資料夾。  選取 **MFC Class From TypeLib** 圖示從右窗格並按一下 **Open**。  
  
3.  在 **Add Class From Typelib Wizard** 對話方塊中，選取一個型別程式庫從 **Available type libraries** 下拉式清單。  **Interfaces** 方塊顯示介面可供這個選取的型別程式庫。  
  
    > [!NOTE]
    >  您可以選取介面從一個以上的型別程式庫。  
  
     若要選取介面，請按兩下或按一下 **Add** 按鈕。  當您這麼做，名稱分派類別將會出現在 **Generated classes** 方塊。  您可以在 `Class` 方塊中輸入類別名稱。  
  
     **File** 方塊顯示類別中宣告的檔案。\(您可以編輯此檔案名稱\)。  如果您想讓在目錄和實作資訊寫在現有檔案或標題刪除專案目錄外，您也可以使用瀏覽按鈕選取其他檔案。  
  
    > [!NOTE]
    >  選取的分派介面的任何類別將放入指定的檔案中。  如果您在不同的標題要介面宣告，您必須執行您要建立的每個標頭檔此精靈。  
  
    > [!NOTE]
    >  陣列型別程式庫資訊在有 .dll、.OCX 或 .OLB 副檔名的檔案會儲存。  
  
4.  按一下 \[**完成**\]。  
  
     使用指定的類別和檔案名稱，精靈會為您的分派類別會撰寫程式碼。  
  
## 請參閱  
 [Automation 用戶端](../mfc/automation-clients.md)