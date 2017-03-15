---
title: "傾印延遲載入的匯入 | Microsoft Docs"
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
  - "延遲載入匯入"
  - "延遲載入匯入, 傾印"
  - "匯入 (延遲載入)"
ms.assetid: f766acf4-9df8-4b85-8cf6-0be3ffc4c124
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 傾印延遲載入的匯入
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

延遲載入的匯入可以利用 [dumpbin \/imports](../../build/reference/imports-dumpbin.md) 傾印，所顯示的資訊與標準匯入稍微不同。  它們被隔離到它們本身 \/imports 傾印的部分，並明確標示為延遲載入的匯入。  如果映像中存在卸載資訊時，會被記下。  如果有繫結資訊存在，目標 DLL 的時間\/日期戳記也會和匯入的繫結位址一起被記下。  
  
## 請參閱  
 [延遲載入 DLL 的連結器支援](../../build/reference/linker-support-for-delay-loaded-dlls.md)