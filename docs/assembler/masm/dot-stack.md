---
title: ".STACK | Microsoft Docs"
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
  - ".STACK"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".STACK directive"
ms.assetid: 70019463-5d4f-41b6-8464-023a8ac2466f
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .STACK
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

搭配使用時 [。模型](../../assembler/masm/dot-model.md)，定義堆疊區段 \(與堆疊的區段名稱\)。  選擇性的`size`指定的堆疊 \(預設值 1024\) 的位元組數目。  `.STACK`指示詞會自動關閉堆疊陳述式。  
  
## 語法  
  
```  
  
.STACK [[size]]  
```  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)