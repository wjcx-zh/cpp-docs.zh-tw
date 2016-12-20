---
title: "無法將建置輸出複製至 Web | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cantcopyoutputstoweb"
ms.assetid: 59cf714b-cf7d-4df9-81ae-d3254969d5bc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 無法將建置輸出複製至 Web
專案系統無法將一個或多個建置輸出檔 \(例如，所建置的 DLL、PDB 或附屬組件\) 複製至 Web 伺服器。  
  
 此錯誤表示一個或多個建置輸出檔未複製至 Web 伺服器。  
  
 如果伺服器上的建置輸出檔遭到鎖定或為唯讀，則通常會發生此錯誤。 如果在伺服器上鎖定檔案，表示 [!INCLUDE[vstecasp](../misc/includes/vstecasp_md.md)] 執行階段未正確地複製目前在伺服器上的組件、附屬組件或偵錯符號。  
  
 伺服器也可能會用盡磁碟空間，或該網路問題可能會防止 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 將檔案上傳至 Web。  
  
### 更正這個錯誤  
  
1.  檢查磁碟空間。  
  
2.  如果鎖定檔案，則重新啟動 Web 伺服器，才能釋放受影響檔案的 [!INCLUDE[vstecasp](../misc/includes/vstecasp_md.md)] 鎖定。  
  
## 請參閱  
 [PDB Files](http://msdn.microsoft.com/zh-tw/1761c84e-8c2c-4632-9649-b5f99964ed3f)