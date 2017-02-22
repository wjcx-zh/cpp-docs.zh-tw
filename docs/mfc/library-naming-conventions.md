---
title: "程式庫命名慣例 | Microsoft Docs"
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
  - "編碼慣例, MFC 程式庫名稱"
  - "主控台應用程式, MFC 程式庫版本"
  - "慣例 [C++], MFC 程式庫名稱"
  - "程式庫 [C++], static"
  - "MFC 程式庫, 命名規範"
  - "NAFXCW.LIB"
  - "NAFXCWD.LIB"
  - "命名慣例 [C++], MFC 目的碼程式庫"
  - "目的碼程式庫"
  - "目的碼程式庫, MFC 命名慣例"
ms.assetid: 39fe7d93-5a14-4c6a-b16c-bf318fa01278
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 程式庫命名慣例
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 物件的程式碼程式庫使用下列命名慣例。  程式庫名稱的格式  
  
 *u*AFX`c`W`d`.LIB  
  
 其中以斜體顯示小寫字母的，是指定名稱的標示，其意義如下表所示：  
  
### 程式庫命名慣例  
  
|指定名稱|值和意義|  
|----------|----------|  
|*u*|ANSI \(N\) 或 Unicode \(U\)|  
|`c`|要建立的專案類型：C\=all|  
|`d`|偵錯或發行：D\=偵錯 \(Debug\)；省略指定名稱\=發行 \(Release\)|  
  
 預設值為建立在 Intel 平台上的偵錯 Windows ANSI 應用程式：NAFXCWD.Lib。  下表列出的所有程式庫是預先建置在 Visual C\+\+ CD\-ROM 的 \\atlmfc\\ lib 目錄中。  
  
### 靜態連結程式庫命名慣例  
  
|程式庫|說明|  
|---------|--------|  
|NAFXCW.LIB|MFC 靜態連結程式庫，發行版本|  
|NAFXCWD.LIB|MFC 靜態連結程式庫，偵錯版本|  
|UAFXCW.LIB|MFC 靜態連結程式庫 \(附 Unicode 支援\)，發行版本|  
|UAFXCWD.LIB|MFC 靜態連結程式庫 \(附 Unicode 支援\)，偵錯版本|  
  
> [!NOTE]
>  如果您需要建立程式庫版本，請查看 \\atlmfc\\src\\mfc 目錄的 Readme.Txt 檔案。  這個檔案會描述使用 NMAKE 提供的 Makefile。  
  
 如需詳細資訊，請參閱 [MFC DLL 的命名慣例](../build/naming-conventions-for-mfc-dlls.md) 和 [MFC 程式庫的 Unicode 版本](../mfc/unicode-in-mfc.md)。  
  
## 請參閱  
 [MFC 程式庫版本](../mfc/mfc-library-versions.md)