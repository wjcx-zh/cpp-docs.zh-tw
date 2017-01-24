---
title: "動態連結程式庫支援 | Microsoft Docs"
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
  - "DLL [C++], MFC"
  - "MFC DLL [C++], 標準 DLL"
  - "NAFXDW.LIB"
  - "NAFXDWD.LIB"
  - "標準 DLL [C++], 專案目標為 DLL"
  - "USRDLL, DLL 支援"
ms.assetid: cc31c69f-3c78-4db1-9ecd-0fd8dc3217e3
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 動態連結程式庫支援
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

NAFXCW.lib 和 NAFXCWD.lib 程式庫 \(列於 [程式庫命名慣例](../mfc/library-naming-conventions.md)的靜態連結程式庫命名慣例資料表\) 建立專案當做動態連結程式庫，可以使用類別庫所建立的應用程式的「標準 DLL」\(原來為「USRDLL」\)。  這個 DLL 支援與 MFCx0.DLL 和 MFCx0D.DLL \(稱為 AFXDLL\)，在 DLL 包含整個類別庫。  如需詳細資訊，請參閱 [DLLs](../build/dlls-in-visual-cpp.md)。  如需 DLL 名稱的表格，請參閱 [MFC 的 DLL 命名慣例](../build/naming-conventions-for-mfc-dlls.md)。  
  
## 請參閱  
 [MFC 程式庫版本](../mfc/mfc-library-versions.md)