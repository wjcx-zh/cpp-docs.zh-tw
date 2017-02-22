---
title: "MFC 通用控制項程式庫的隔離 | Microsoft Docs"
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
  - "MFC, 通用控制項程式庫"
ms.assetid: 7471e6f0-49b0-47f7-86e7-8d6bc3541694
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# MFC 通用控制項程式庫的隔離
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通用控制項程式庫在 MFC 中現在是隔離的，可讓不同的模組 \(例如使用者 DLL\) 使用通用控制項程式庫的不同版本藉由指定版本在其資訊清單中。  
  
 MFC 應用程式 \(或 MFC 呼叫使用者程式碼\) 呼叫通用控制項程式庫 API 以包裝函式名稱 `Afx`*FunctionName*，其中 *FunctionName* 是控制項公用應用程式開發介面的名稱。  這些包裝函式在 afxcomctl32.h 和 afxcomctl32.inl 定義。  
  
 您可以使用 [AFX\_COMCTL32\_IF\_EXISTS](../Topic/AFX_COMCTL32_IF_EXISTS.md) 和 [AFX\_COMCTL32\_IF\_EXISTS2](../Topic/AFX_COMCTL32_IF_EXISTS2.md) 巨集 \(定義於 afxcomctl32.h\) 判斷通用控制項程式庫是否實作某應用程式開發介面而不是呼叫 [GetProcAddress](../build/getprocaddress.md)。  
  
 技術上來說，正在呼叫通用控制項程式庫 API 以包裝函式類別， `CComCtlWrapper` \(定義於 afxcomctl32.h\)。  `CComCtlWrapper` 對載入和卸載也負責 comctl32.dll。  MFC 模組狀態包含指標為 `CComCtlWrapper`執行個體。  您可以使用 `afxComCtlWrapper` 巨集來存取包裝函式類別。  
  
 請注意直接呼叫公用控制應用程式開發介面的， \(不使用 MFC 包裝函式\) 從 MFC 應用程式或使用者 DLL 在許多情況下，會運作，因為它在其資訊清單中要求\) 的 MFC 應用程式或使用者 DLL 繫結至通用控制項程式庫。  不過，，因為 MFC 程式碼可能會以不同的通用控制項程式庫版本，使用者的 DLL 呼叫 MFC 程式碼必須使用包裝函式。