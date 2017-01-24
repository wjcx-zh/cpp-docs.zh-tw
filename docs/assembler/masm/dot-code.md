---
title: ".CODE | Microsoft Docs"
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
  - ".CODE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".CODE directive"
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .CODE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

搭配使用時 [。模型](../../assembler/masm/dot-model.md)，表示這段程式碼片段的開頭。  
  
## 語法  
  
```  
.CODE [[name]]  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|`name`|指定的程式碼的區段名稱的選擇性參數。  預設名稱是很小，小，光碟，和一般的 \_TEXT [模型](../../assembler/masm/dot-model.md)。  預設名稱是 *modulename*而有些款式的 \_TEXT。|  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)   
 [.DATA](../../assembler/masm/dot-data.md)