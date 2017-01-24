---
title: "無法同時指定 /win32icon 和 /win32resource | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc2023"
  - "bc2023"
helpviewer_keywords: 
  - "BC2023"
ms.assetid: 60914807-1fde-4fef-9c6f-6f4a62527eed
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法同時指定 /win32icon 和 /win32resource
`/win32resource` 和 `/win32icon` 選項互斥，因為兩者都會將圖示資訊插入輸出檔中。  
  
 **錯誤 ID︰**BC2023  
  
### 更正這個錯誤  
  
-   只使用 `/win32icon` 選項將 .ico 檔插入輸入檔中。 這個 .ico 檔表示 Windows 檔案總管中的輸出檔。  
  
     — 或 —  
  
-   只使用 `/win32resource` 選項將 Win32 資源檔插入輸入檔中。 Win32 資源可以包含版本或點陣圖 \(圖示\) 資訊，這項資訊可以協助您在 Windows 檔案總管中識別應用程式。  
  
## 請參閱  
 [\/win32icon](../Topic/-win32icon.md)   
 [\/win32resource](../Topic/-win32resource.md)