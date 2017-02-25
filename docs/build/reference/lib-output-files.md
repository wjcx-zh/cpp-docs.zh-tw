---
title: "LIB 輸出檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Lib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "輸出檔, LIB"
ms.assetid: e73d2f9b-a42d-402b-b7e3-3a94bebb317e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# LIB 輸出檔案
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

LIB 產生的輸出檔案會根據使用的模式而有所不同，如下表所示。  
  
|模式|Output|  
|--------|------------|  
|預設模式 \(建置或修改程式庫\)|COFF 程式庫 \(.lib\)|  
|以 \/EXTRACT 引出一個成員|目的檔 \(.obj\)|  
|以 \/DEF 建置匯出檔案和匯入程式庫|匯入程式庫 \(.lib\) 和匯出檔案 \(.exp\)|  
  
## 請參閱  
 [LIB 概觀](../../build/reference/overview-of-lib.md)