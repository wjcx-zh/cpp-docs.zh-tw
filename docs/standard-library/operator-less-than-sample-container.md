---
title: "operator&lt; (&lt;sample container&gt;) | Microsoft Docs"
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
  - "std::operator<"
  - "operator<"
  - "std.<"
  - "<"
  - "std.operator<"
  - "std::<"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "< 運算子"
  - "< 運算子, 比較特定物件"
  - "運算子 <, valarrays"
  - "operator<, valarrays"
ms.assetid: 31027dd6-53be-428b-b950-1dcb25393597
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# operator&lt; (&lt;sample container&gt;)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  本主題將 Visual C\+\+ 文件做為用於 Standard C\+\+ 程式庫的容器的非執行的範例。  如需詳細資訊，請參閱 [STL 容器](../standard-library/stl-containers.md)。  
  
 多載比較範本兩個物件的 **operator\<** 把 [容器](../standard-library/sample-container-class.md)。  
  
## 語法  
  
```  
  
   template<class Ty>  
bool operator<(  
   const Container <Ty>& _Left,  
   const Container <Ty>& _Right  
);  
```  
  
## 傳回值  
 傳回 `lexicographical_compare`\(\_Left。  [啟動](../standard-library/container-class-begin.md)， \_Left。  [結束](../standard-library/container-class-end.md)， \_Right**.begin**， \_Right。**end**\)。  
  
## 請參閱  
 [\<sample container\>](../standard-library/sample-container.md)