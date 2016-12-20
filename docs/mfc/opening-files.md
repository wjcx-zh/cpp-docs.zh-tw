---
title: "開啟檔案 | Microsoft Docs"
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
  - "CFile 類別, 變數"
  - "範例 [MFC], 開啟檔案"
  - "例外狀況處理 [C++], 開啟檔案"
  - "例外狀況處理 [C++], 當開啟檔案時"
  - "檔案物件 [C++]"
  - "檔案 [C++], 開啟"
  - "MFC [C++], 檔案作業"
  - "Open 呼叫"
  - "Open 成員函式"
  - "Open 方法, CFile 類別"
  - "開啟檔案"
  - "開啟檔案, 例外狀況處理"
  - "開啟檔案, 在 MFC 中"
ms.assetid: a991b8ec-b04a-4766-b47e-7485b5dd0b01
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 開啟檔案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 MFC 中，開啟檔案的最常見的方式是兩階段的程序。  
  
#### 開啟檔案  
  
1.  建立檔案物件，而不指定路徑或使用權限旗標。  
  
     您通常藉由在堆疊框架宣告 [CFile](../mfc/reference/cfile-class.md) 變數建立檔案物件。  
  
2.  對檔案物件呼叫 [Open](../Topic/CFile::Open.md) 成員函式，提供路徑和使用權限旗標。  
  
     如果已成功開啟檔案，`Open` 的傳回值會是非零，或 0 如果無法開啟指定的檔案。  `Open` 成員函式原型如下:  
  
     `virtual BOOL Open( LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL );`  
  
     開啟旗標指定您想要檔案的使用權限，例如唯讀。  可能的旗標值定義在 `CFile` 類別中的列舉常數，使其符合"`CFile::`" 如 `CFile::modeRead`。  如果您要建立檔案，請使用 `CFile::modeCreate` 旗標。  
  
 下列範例顯示如何建立具有讀取\/寫入權限的新檔案 \(取代任何之前具有相同路徑的檔案\):  
  
 [!code-cpp[NVC_MFCFiles#1](../mfc/codesnippet/CPP/opening-files_1.cpp)]  
  
> [!NOTE]
>  這個範例會建立並開啟檔案。  如果有問題， `Open` 可能會呼叫在它的最後一個參數的 `CFileException` 物件，如下所示。  `TRACE` 巨集列印表示失敗的檔案名稱和程式碼原因。  如果您需要更詳細的錯誤報告，您可以呼叫 `AfxThrowFileException` 函式。  
  
## 請參閱  
 [CFile Class](../mfc/reference/cfile-class.md)   
 [CFile::Open](../Topic/CFile::Open.md)   
 [檔案](../mfc/files-in-mfc.md)