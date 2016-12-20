---
title: "Changing the Names of Symbol Header Files | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.symbol.changing.header"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resource files, multiple"
  - "Resource Includes dialog box"
  - "symbol header files, changing names"
  - "symbol header files"
  - "header files, changing names"
  - "names [C++], symbol header files"
  - "symbols, symbol header files"
  - "Resource.h"
ms.assetid: b948284a-7899-402e-ab12-9f2c8480ca9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Changing the Names of Symbol Header Files
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通常會在 Resource.h 中儲存所有符號定義。  不過，您可能需要變更這 Include 檔案名稱，好讓您可以，比方說在相同目錄中處理多個資源檔。  
  
### 變更資源符號標頭檔名稱  
  
1.  在 \[[資源檢視](../windows/resource-view-window.md)\] 中，以滑鼠右鍵按一下 .rc 檔，然後從捷徑功能表選擇 \[[資源包含](../windows/resource-includes-dialog-box.md)\]。  
  
    > [!NOTE]
    >  如果您的專案尚未包含 .rc 檔，請參閱[建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在 \[**符號標頭檔**\] 方塊中，輸入 Include 檔案的新名稱。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。  
  
 需求  
  
 Win32  
  
## 請參閱  
 [Viewing Resource Symbols](../windows/viewing-resource-symbols.md)   
 [Predefined Symbol IDs](../windows/predefined-symbol-ids.md)