---
title: "AFXDLL 版本 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "afxdll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AFXDLL 程式庫"
  - "應用程式精靈 [C++], 預設會使用 AFXDLL"
  - "MFC 的 DLL 版本 [C++]"
  - "MFC [C++], AFXDLL 版本"
  - "MFC DLL [C++], 動態連結至程式庫"
  - "MFC 程式庫 [C++], 動態連結"
ms.assetid: c078ae8f-85a9-43cb-9ded-c09ca2c45723
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AFXDLL 版本
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

而不需要建立自己的應用程式將靜態連結至 MFC 物件程式碼程式庫，您可以建立自己的應用程式使用其中一個 AFXDLL 程式庫，在 MFC DLL 包含多個執行中的應用程式可以共用。  如需 AFXDLL 的表格，請參閱 [DLL:命名慣例](../build/naming-conventions-for-mfc-dlls.md)。  
  
> [!NOTE]
>  根據預設， MFC 應用程式精靈建立 AFXDLL 專案。  若要使用靜態連結至 MFC 程式碼，請將 MFC 應用程式精靈的 **Use MFC in a static library** 選項。  靜態連接是在 Visual C\+\+ 的標準版中無法使用。  
  
## 請參閱  
 [MFC 程式庫版本](../mfc/mfc-library-versions.md)