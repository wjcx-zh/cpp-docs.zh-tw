---
title: "命令巨集和選項巨集 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NMAKE 中的命令巨集"
  - "巨集, 命令巨集"
  - "巨集, 選項巨集"
  - "選項巨集"
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 命令巨集和選項巨集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft 產品的命令巨集為預先定義的。  選項巨集代表這些產品的選項，且預設為未定義。  兩者都使用於預先定義的推斷規則，並且可以使用在描述區塊或使用者定義的推斷規則中。  可重新定義命令巨集代表部分或全部的命令列，包含選項在內。  如果未定義選項巨集，選項巨集會產生 null 字串。  
  
|Microsoft 產品|命令巨集|定義為|選項巨集|  
|------------------|----------|---------|----------|  
|巨集組合語言|**AS**|ml|**AFLAGS**|  
|Basic 編譯器|**BC**|bc|**BFLAGS**|  
|C 編譯器|**CC**|cl|**CFLAGS**|  
|C\+\+ 編譯器|**CPP**|cl|**CPPFLAGS**|  
|C\+\+ 編譯器|**CXX**|cl|**CXXFLAGS**|  
|資源編譯器|**RC**|rc|**RFLAGS**|  
  
## 請參閱  
 [特殊的 NMAKE 巨集](../build/special-nmake-macros.md)