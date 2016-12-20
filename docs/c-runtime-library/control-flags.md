---
title: "控制旗標 | Microsoft Docs"
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
  - "c.flags"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "偵錯堆積, 控制旗標"
  - "旗標, 控制項"
  - "堆積配置, 控制旗標"
ms.assetid: 8dbd24a5-0633-42d1-9771-776db338465f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 控制旗標
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft C 執行階段程式庫的偵錯版本會使用下列旗標控制堆疊配置和報告流程。  如需詳細資訊，請參閱[CRT 偵錯技術](../Topic/CRT%20Debugging%20Techniques.md)。  
  
|旗標|說明|  
|--------|--------|  
|[\_CRTDBG\_MAP\_ALLOC](../c-runtime-library/crtdbg-map-alloc.md)|將基底堆積函式對其偵錯版本對應項。|  
|[\_DEBUG](../c-runtime-library/debug.md)|啟用執行階段函式的偵錯版本|  
|[\_crtDbgFlag](../c-runtime-library/crtdbgflag.md)|控制偵錯堆積管理員如何追蹤配置|  
  
 這些旗標可以定義使用 \/D 命令列選項或以 `#define` 指示詞。  當旗標定義與 `#define`時，指示詞必須顯示，在定期宣告之前標頭檔包含陳述式。  
  
## 請參閱  
 [全域變數和標準類型](../c-runtime-library/global-variables-and-standard-types.md)