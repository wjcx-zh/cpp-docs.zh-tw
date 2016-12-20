---
title: "資源編譯器錯誤 RC2148 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC2148"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2148"
ms.assetid: 0290065c-35d3-4815-80c5-40bf7132ae1d
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 資源編譯器錯誤 RC2148
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

SUBLANGUAGE ID 太大  
  
 SUBLANGUAGE ID 值超出範圍。  
  
 **LANGUAGE** 陳述式必須使用下列語法：  
  
 **LANGUAGE** *primary\_language\_ID*,*secondary\_language\_ID*  
  
 有效的 SUBLANGUAGE ID 在 WINNT.h 檔案中定義為 **SUBLANG\_** 常數。