---
title: "LIB 輸入檔 | Microsoft Docs"
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
  - "Lib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "輸入檔, LIB"
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# LIB 輸入檔
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

LIB 需要的輸入檔案會根據使用的模式而有所不同，如下表所示：  
  
|模式|輸入|  
|--------|--------|  
|預設模式 \(建置或修改程式庫\)|COFF 目的檔 \(.obj\)、COFF 程式庫 \(.lib\)、32 位元物件模型格式 \(Object Model Format，OMF\) 目的檔 \(.obj\)|  
|以 \/EXTRACT 引出一個成員|COFF 程式庫 \(.lib\)|  
|以 \/DEF 建置匯出檔案和匯入程式庫|模組定義檔案 \(Module\-Definition File，.def\)、COFF 目的檔 \(.obj\)、COFF 程式庫 \(.lib\)、32 位元 OMF 目的檔 \(.obj\)|  
  
> [!NOTE]
>  16 位元版本的 LIB 所建立的 OMF 程式庫不能當做 32 位元版本的 LIB 的輸入。  
  
## 請參閱  
 [LIB 概觀](../../build/reference/overview-of-lib.md)