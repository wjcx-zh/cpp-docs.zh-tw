---
title: "MFC DLL 命名慣例 | Microsoft Docs"
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
  - "DLL [C++], 程式庫名稱"
  - "DLL [C++], 命名規範"
  - "程式庫 [C++], 名稱"
  - "MFC DLL [C++], 命名規範"
  - "MFC 程式庫 [C++], 命名規範"
  - "命名慣例 [C++], MFC DLL"
  - "共用的 DLL 版本 [C++]"
ms.assetid: 0db9c3f3-87d3-40e8-8964-250f9d2a2209
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# MFC DLL 命名慣例
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包含在 MFC 的 DLL 和程式庫會依照結構化命名慣例。  這讓您很容易知道您應該使用哪一個 DLL 或程式庫。  
  
 建置使用這些 DLL 的應用程式或擴充 DLL 所需的匯入程式庫，其主檔名 \(Base Name\) 與 DLL 相同，但是多了 .lib 的副檔名。  
  
### 共用 DLL 命名慣例  
  
|DLL|說明|  
|---------|--------|  
|MFCx0.DLL|MFC DLL、ANSI 發行版本 \(Release Version\)|  
|MFCx0U.DLL|MFC DLL、Unicode 發行版本|  
|MFCx0D.DLL|MFC DLL、ANSI 偵錯版本|  
|MFCx0UD.DLL|MFC DLL、Unicode 偵錯版本|  
  
 如果您是動態地連結至共用的 MFC DLL 版本 \(無論是來自應用程式或擴充 DLL\)，您必須要在產品中包含 MFCx0.DLL。  如果您需要在應用程式中加入 Unicode 支援，請改包含 MFCx0U.DLL。  
  
 如果您是靜態地將 DLL 連結至 MFC，您必須將它與其中一個靜態 MFC 程式庫連結。  這些版本是根據 \[N&#124;U\]AFXCW\[D\].LIB 慣例來命名。  如需詳細資訊，請參閱[程式庫命名慣例](../mfc/library-naming-conventions.md) \(MFC\) 裡的表格「靜態連結程式庫的命名慣例」。  
  
 如需可以與應用程式一起散發的 Visual C\+\+ DLL 清單，請參閱您所安裝 Visual Studio 中的 Redist.txt。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [程式庫命名慣例](../mfc/library-naming-conventions.md)  
  
## 請參閱  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)