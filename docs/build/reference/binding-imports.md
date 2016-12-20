---
title: "繫結匯入 | Microsoft Docs"
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
  - "/DELAY:NOBIND 連結器選項"
  - "DELAY:NOBIND 連結器選項"
ms.assetid: bb766038-deb1-41b1-bcbc-29a30e8c1e2a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 繫結匯入
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

預設的連結器行為是為延遲載入的 DLL 建立一個可繫結的匯入位址表。  如果已繫結 DLL，Helper 函式將嘗試以繫結資訊取代呼叫每一個參考匯入的 **GetProcAddress**。  如果時間戳記或是慣用位址與載入之 DLL 的資料不符，Helper 函式將假設繫結匯入位址表已過期而繼續進行，好像該表並不存在。  
  
 如果您不打算繫結 DLL 的延遲載入匯入，則在連結器的命令行中指定 [\/delay](../../build/reference/delay-delay-load-import-settings.md):nobind 可以避免產生繫結匯入位址表而耗費影像檔中的空間。  
  
## 請參閱  
 [延遲載入 DLL 的連結器支援](../../build/reference/linker-support-for-delay-loaded-dlls.md)