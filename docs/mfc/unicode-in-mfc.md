---
title: "MFC 中的 Unicode | Microsoft Docs"
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
  - "字串 [C++], Unicode"
  - "Unicode [C++], 啟用"
  - "Unicode [C++], MFC"
  - "寬字元, 編碼"
  - "寬字元, Unicode"
ms.assetid: 1002004b-4113-4380-bf63-e1570934b793
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# MFC 中的 Unicode
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 支援 Windows NT、Windows 2000 和 Windows XP 平台上編碼寬字元的 Unicode 標準。  Unicode 應用程式在 Windows 98 平台上無法執行。  
  
 MFC 程式庫的 Unicode 版本如下:  
  
### 靜態連結程式庫。  
  
|Release|偵錯|說明|  
|-------------|--------|--------|  
|UAFXCW.lib, .pdb|UAFXCWD.lib, .pdb|Unicode MFC 靜態連結程式庫|  
  
### 動態連結程式庫。  
  
|Release|偵錯|說明|  
|-------------|--------|--------|  
|MFC100U.lib, .dbg, def, .dll, .map, .pdb, .prf|MFC100UD.lib, .def, .dll, .map, .pdb|Unicode MFC 匯入程式庫 \(為副檔名的說明請參閱下面的備註\)|  
|MFCS100U.lib, .pdb|MFCS100UD.lib, .pdb|Unicode MFC 包含在應用程式或 DLL 必須以靜態方式連結的程式碼的匯入程式庫。|  
  
 **檔案類型**  
  
-   匯入程式庫檔案的副檔名 \(.lib\)。  
  
-   動態連結程式庫檔案的副檔名 \(.dll\)。  
  
-   模組定義 \(.def\) 檔是包含定義的 .exe 或 .dll 陳述式的文字檔。  
  
-   對應 \(.map\) 檔是包含資訊連結器使用，在連結程式的文字檔。  
  
-   程式庫 \(.lib\) 檔案與 MFC DLL 版本搭配使用。  這些檔案會在應用程式或 DLL 必須以靜態方式連結的程式碼。  
  
-   程式資料庫 \(.pdb\) 檔案會包含偵錯和專案狀態資訊。  
  
-   偵錯 \(.dbg\) 檔案包含 Visual C\+\+ 偵錯工具使用的相關資訊 \(COFF FPO 和 CodeView\)。  
  
 如需命名慣例的詳細資訊，請參閱 [程式庫命名慣例](../mfc/library-naming-conventions.md)。  
  
 如需使用 Unicode 和 MFC 的詳細資訊，請參閱 [字串:Unicode 和多位元組字元集 \(MBCS\) 支援](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。  
  
## 請參閱  
 [概念](../mfc/mfc-concepts.md)   
 [一般 MFC 主題](../mfc/general-mfc-topics.md)