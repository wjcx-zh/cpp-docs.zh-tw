---
title: "Platform::CallbackContext 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::CallbackContext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::CallbackContext 列舉"
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 3
---
# Platform::CallbackContext 列舉
指定回呼函式 \(事件處理常式\) 會執行的執行緒內容。  
  
## 語法  
  
```cpp  
enum class CallbackContext {};  
```  
  
## Members  
  
|類型程式碼|描述|  
|-----------|--------|  
|任何|回呼函式可以在任何執行緒的內容中執行。|  
|相同|回呼函式只能在啟動非同步作業的執行緒內容中執行。|  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**platform.winmd