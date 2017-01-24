---
title: "為您的自訂類別多載 &gt;&gt; 運算子 | Microsoft Docs"
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
  - "運算子 >>, 為您的自訂類別多載"
  - "運算子 >>"
  - "運算子 >>, 為您的自訂類別多載"
ms.assetid: 40dab4e0-3f97-4745-9cc8-b86e740fa246
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 為您的自訂類別多載 &gt;&gt; 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

輸入資料流為標準型別用來擷取 \(`>>`\) 運算子。  您可以為型別撰寫類似的提取運算子;您的成功取決於精確使用泛空白字元。  
  
 擷取這個運算子的範例之前顯示的 `Date` 類別的:  
  
```  
istream& operator>> ( istream& is, Date& dt )  
{  
   is >> dt.mo >> dt.da >> dt.yr;  
   return is;  
}  
```  
  
## 請參閱  
 [輸入資料流](../standard-library/input-streams.md)