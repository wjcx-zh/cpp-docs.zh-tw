---
title: "複合陳述式 (區塊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "}"
  - "{"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "區塊, 關於區塊"
  - "複合陳述式"
ms.assetid: 23855939-7430-498e-8936-0c70055ea701
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 複合陳述式 (區塊)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

複合陳述式是由包含在大括號 \(**{ }**\) 內的零個或多個陳述式所組成。  複合陳述式可以在必須有陳述式的任何位置使用。  複合陳述式通常稱為「區塊」\(Block\)。  
  
## 語法  
  
```  
  
{ [ statement-list ] }  
```  
  
## 備註  
 下列範例會使用複合陳述式做為 **if** 陳述式的 *statement* 部分 \(如需有關此語法的詳細資訊，請參閱 [if 陳述式](../cpp/if-else-statement-cpp.md)\)：  
  
```  
if( Amount > 100 )  
{  
    cout << "Amount was too large to handle\n";  
    Alert();  
}  
else  
    Balance -= Amount;  
```  
  
> [!NOTE]
>  由於宣告是陳述式，因此宣告可以是 *statement\-list* 中的其中一個陳述式。  因此，在複合陳述式內宣告，但未明確宣告為靜態的名稱，會具有區域範圍和 \(為物件時\) 存留期。  如需如何處理具有區域範圍之名稱的詳細資訊，請參閱[範圍](../cpp/scope-visual-cpp.md)。  
  
## 請參閱  
 [C\+\+ 陳述式概觀](../cpp/overview-of-cpp-statements.md)