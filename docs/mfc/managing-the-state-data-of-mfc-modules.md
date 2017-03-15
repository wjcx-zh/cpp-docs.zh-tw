---
title: "管理 MFC 模組的狀態資料 | Microsoft Docs"
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
  - "資料管理 [C++]"
  - "資料管理 [C++], MFC 模組"
  - "匯出的介面和全域狀態 [C++]"
  - "全域狀態 [C++]"
  - "MFC [C++], 管理狀態資料"
  - "還原的模組狀態"
  - "模組狀態, 儲存和還原"
  - "多個模組"
  - "視窗程序進入點 [C++]"
ms.assetid: 81889c11-0101-4a66-ab3c-f81cf199e1bb
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 管理 MFC 模組的狀態資料
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文將討論 MFC 模組狀態資料，而這個狀態如何更新，當執行 \(路徑程式碼透過應用程式接受，當執行\) 輸入處理序並讓模組。  與 `AFX_MANAGE_STATE` 和 `METHOD_PROLOGUE` 巨集的開啟或關閉模組狀態也會討論。  
  
> [!NOTE]
>  這個詞彙「module」這裡提到的可執行程式，或者對 DLL \(或一組 DLL\) 獨立應用程式的其他部分運作，不過，使用 MFC DLL 的共用複本。  ActiveX 控制項是模組的一般範例。  
  
 如下圖所示， MFC 具有狀態資料應用程式的每個模組。  這個範例的資料包含視窗執行個體控制代碼 \(用於載入資源\)，指向應用程式目前的 `CWinApp` 和 `CWinThread` 物件， OLE 模組參考計數和維護視窗物件控制代碼和 MFC 物件之間的對應執行個體連接的各種對應。  然而，在中，當應用程式使用多個模組時，每個模組狀態資料不是全應用程式。  相反地，每個模組都有自己的 MFC 狀態資料的私用複本。  
  
 ![單一模組 &#40;應用程式&#41; 的狀態資料](../mfc/media/vc387n1.png "vc387N1")  
單一模組 \(應用程式\) 的狀態資料  
  
 模組的狀態資料儲存在結構中並透過指標永遠可供該結構。  如下圖所示，當執行流程輸入特定模組，模組的狀態必須是「Current」或「的有效狀態。  因此，每個執行緒物件具有指標對該應用程式啟用的狀態結構。  保留這個指標一直會更新為處理應用程式的全域狀態和維護每個模組的狀態完整性很重要。  全域狀態的有效管理可能會導致無法預期的應用程式行為。  
  
 ![多個模組的狀態資料](../mfc/media/vc387n2.png "vc387N2")  
多個模組的狀態資料  
  
 也就是說，每個模組為正確的交換負責在模組狀態之間它的進入點。  「進入點」是執行流程可以輸入模組的程式碼中的位元。  進入點包括:  
  
-   [在 DLL 的匯出函式](../mfc/exported-dll-function-entry-points.md)  
  
-   [COM 介面的成員函式](../mfc/com-interface-entry-points.md)  
  
-   [視窗程序](../mfc/window-procedure-entry-points.md)  
  
## 請參閱  
 [一般 MFC 主題](../mfc/general-mfc-topics.md)