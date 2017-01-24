---
title: "operator!= | Microsoft Docs"
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
  - "std::!="
  - "!="
  - "std::operator!="
  - "std.operator!="
  - "std.!="
  - "operator!="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "!= 運算子"
  - "運算子 !="
  - "operator!="
ms.assetid: ef2be7f0-1c94-4edc-b65c-731fddd519f4
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# operator!=
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  本主題將 Visual C\+\+ 文件做為用於 Standard C\+\+ 程式庫的容器的非執行的範例。  如需詳細資訊，請參閱 [STL 容器](../standard-library/stl-containers.md)。  
  
 多載比較樣板類別 [容器](../standard-library/sample-container-class.md)兩個物件的 `operator!=` 。  
  
## 語法  
  
```  
  
   template<class Ty>  
bool operator!=(  
   const Container <Ty>& _Left,  
   const Container <Ty>& _Right  
);  
```  
  
## 傳回值  
 傳回 **\!**\(\_Left **\=\=** `_Right`\)。  
  
## 請參閱  
 [\<sample container\>](../standard-library/sample-container.md)