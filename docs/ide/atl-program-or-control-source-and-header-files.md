---
title: "ATL 程式或控制項原始程式檔和標頭檔 | Microsoft Docs"
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
  - "檔案類型 [C++], ATL 原始檔和標頭檔"
ms.assetid: cb65372f-4880-4007-b582-a52eaa568fd1
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL 程式或控制項原始程式檔和標頭檔
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

根據您為所建立專案選取的選項，當您在 Visual Studio 中建立 ATL 專案時會建立下列檔案。  
  
 這些檔案都是位於 *Projname* 目錄中，和 \[方案總管\] 中的標頭檔 \(.h 檔\) 資料夾或原始程式檔 \(.cpp 檔\) 資料夾。  
  
|檔案名稱|描述|  
|----------|--------|  
|*Projname*.h|主包含檔，包含 C\+\+ 介面定義和 ATLSample.idl 所定義項目的 GUID 宣告，  它是由 MIDL 在編譯期間重新產生的。|  
|*Projname*.cpp|主程式原始程式檔，  它包含同處理序伺服程式 \(In\-Process Server\) 的 DLL 匯出實作和本機伺服程式 \(Local Server\) 的 `WinMain` 實作。  這還會針對服務來實作所有服務管理函式。|  
|Resource.h|資源檔的標頭檔 \(Header File\)。|  
|StdAfx.cpp|包含 StdAfx.h 和 Atlimpl.cpp 檔案。|  
|StdAfx.h|包含 ATL 標頭檔。|  
  
## 請參閱  
 [為 Visual C\+\+ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)   
 [MFC 程式或控制項原始程式檔和標頭檔](../ide/mfc-program-or-control-source-and-header-files.md)   
 [CLR 專案](../ide/files-created-for-clr-projects.md)