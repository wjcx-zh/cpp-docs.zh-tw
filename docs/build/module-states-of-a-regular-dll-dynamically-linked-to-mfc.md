---
title: "動態連結至 MFC 之標準 DLL 的模組狀態 | Microsoft Docs"
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
  - "DLL [C++], 模組狀態"
  - "MFC DLL [C++], 標準 DLL"
  - "模組狀態 [C++]"
  - "模組狀態 [C++], 標準 DLL 動態連結"
  - "標準 DLL [C++], 動態連結至 MFC"
ms.assetid: b4493e79-d25e-4b7f-a565-60de5b32c723
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 動態連結至 MFC 之標準 DLL 的模組狀態
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

動態地將標準 DLL 連結到 MFC DLL 的能力，可以產生一些非常複雜的組態。  例如，標準 DLL 和使用它的可執行檔都可以動態地連結至 MFC DLL 和任何擴充 DLL。  
  
 這個組態會顯露與 MFC 全域資料有關的問題，例如指向目前 `CWinApp` 物件的指標和控制代碼對應等等。  
  
 在 MFC 4.0 版之前，這個全域資料位於 MFC DLL 之中，並且由處理序 \(Process\) 中所有的模組共用。  因為每個處理序會使用 Win32 DLL 取得自己的 DLL 資料複本，所以這個配置提供簡便的方式來追蹤每個處理序的資料。  此外，因為 AFXDLL 模型假設只會有一個 `CWinApp` 物件，而且處理序中只有一組控制代碼對應，所以這些項目可以在 MFC.DLL 本身中追蹤。  
  
 但是現在有了可將標準 DLL 動態連結至 MFC DLL 的功能，處理序便可以擁有兩個或更多的 `CWinApp` 物件─和兩組或更多的控制代碼對應。  MFC 要怎樣儲存其應使用的控制代碼對應呢？  
  
 解決方法是給予每個模組 \(應用程式或標準 DLL\) 它自己的全域狀態資訊的複本。  因此，標準 DLL 的 **AfxGetApp** 呼叫會傳回 DLL 的 `CWinApp` 物件指標，而不是在可執行檔的那一個。  這種 MFC 全域資料的每個模組複本，稱為模組狀態，在 [MFC Tech Note 58](../mfc/tn058-mfc-module-state-implementation.md) 中會說明。  
  
 MFC 通用視窗程序會自動地轉換到正確的模組狀態，因此在標準 DLL 中實作的任何訊息處理常式都不需擔心。  然而當您的可執行檔呼叫到標準 DLL 時，您需要明確地將目前模組狀態設定為 DLL 的那一個。  若要達到這個目的，請在每個由 DLL 匯出的函式中使用 **AFX\_MANAGE\_STATE** 巨集。  這個部分可藉由將下行程式碼加入由 DLL 匯出的函式開頭來完成：  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [管理 MFC 模組的狀態資料](../mfc/managing-the-state-data-of-mfc-modules.md)  
  
-   [動態連結至 MFC 的標準 DLL](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [擴充 DLL](../build/extension-dlls-overview.md)  
  
## 請參閱  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)