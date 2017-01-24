---
title: "MFC DLL 精靈產生的類別和函式 | Microsoft Docs"
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
  - "類別 [C++], 由 MFC DLL 精靈產生"
  - "程式碼 [C++], 由 MFC DLL 精靈產生"
  - "DLL [C++], 精靈類別和函式"
  - "函式 [MFC]"
  - "函式 [MFC], DLL"
  - "MFC DLL 精靈"
ms.assetid: e69e62fe-4953-42bf-a2fc-50bbf9bdaeaf
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC DLL 精靈產生的類別和函式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MFC DLL 精靈產生的程式碼會視建立的 DLL 類型和所選取的選項而定。  MFC DLL 精靈會為兩種一般 DLL 產生相同的程式碼。  
  
|DLL 的類型|選項|類別|函式|  
|-------------|--------|--------|--------|  
|[副檔名](../../build/extension-dlls-overview.md)|無|無|`DllMain`|  
|[Regular](../../build/regular-dlls-dynamically-linked-to-mfc.md)|無|衍生自 `CWinApp` 的應用程式類別|無|  
|[Regular](../../build/regular-dlls-dynamically-linked-to-mfc.md)|Automation|衍生自 `CWinApp` 的應用程式類別|**DllGetClassObjectDllCanUnloadNowDllRegisterServer**|  
|[副檔名](../../build/extension-dlls-overview.md)|Window Sockets|無|`DllMain`|  
|[Regular](../../build/regular-dlls-dynamically-linked-to-mfc.md)|Window Sockets|衍生自 `CWinApp` 的應用程式類別|`InitInstance` 包含呼叫 `AfxSocketInit`|  
  
## 請參閱  
 [MFC DLL 精靈](../../mfc/reference/mfc-dll-wizard.md)