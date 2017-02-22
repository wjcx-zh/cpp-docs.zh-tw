---
title: "EXTERNDEF | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EXTERNDEF"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EXTERNDEF directive"
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# EXTERNDEF
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

定義一或多個外部變數、 標籤或呼叫的符號*名稱*型別是`type`。  
  
## 語法  
  
```  
  
EXTERNDEF [[langtype]] name:type [[, [[langtype]] name:type]]...  
```  
  
## 備註  
 如果*名稱* 定義在模組中，則會被視為 [公用](../../assembler/masm/public-masm.md)。  如果*名稱* 參考本單元，它會被視為  [EXTERN](../../assembler/masm/extern-masm.md)。  如果*名稱*是未被參考，則會忽略它。  `type`可以是 [ABS](../../assembler/masm/operator-abs.md)，哪一個匯入*名稱*做為常數。  通常使用在加入檔案。  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)