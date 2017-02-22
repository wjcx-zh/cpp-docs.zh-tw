---
title: "UNIX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "unix"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "POSIX 相容性"
  - "POSIX 檔名"
  - "UNIX"
  - "UNIX, 相容性"
ms.assetid: 40792414-7a5b-415d-bfa8-2bfb1ebb3731
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# UNIX
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您打算將程式移到 UNIX，請遵循以下方針:  
  
-   不要從 SYS 子目錄刪除標頭檔。  只有在您不打算將專案發行到 UNIX 程式時，您可以在其他地方放置 SYS 標頭檔。  
  
-   使用 Unix 相容路徑分隔符號採用表示路徑和檔案名稱的字串做為引數的常式。  UNIX 因此只支援正斜線 \(\/\)，而 Win32 作業系統支援反斜線 \(\\\) 或正斜線 \(\/\)。  例如，本文件使用 Unix 相容斜線在 `#include` 陳述式當路徑分隔的符號。\(不過， Windows 作業系統的命令提示字元中， CMD.EXE，不支援在命令的正斜線輸入在命令提示字元\)。  
  
-   使用在 UNIX 正確運作，區分大小寫的路徑和檔名。  在 Win32 作業系統的檔案配置表 \(FAT\) 檔案系統不區分大小寫;目錄清單，但是會忽略大小寫的 NTFS 檔案系統保留方塊在檔案搜尋和其他系統作業。  
  
    > [!NOTE]
    >  本版本的 Visual C\+\+， 已從函式描述取消UNIX 相容性資訊。  
  
## 請參閱  
 [相容性](../c-runtime-library/compatibility.md)