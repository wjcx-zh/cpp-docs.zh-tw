---
title: "建構輸入資料流物件 | Microsoft Docs"
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
  - "輸入資料流物件"
ms.assetid: ab94866e-6ffe-4f15-b4db-0bd23e636075
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 建構輸入資料流物件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您只使用 `cin` 物件，您並不需要建構輸入資料流。  因此，如果您使用，您必須建構輸入資料流:  
  
-   [輸入檔案資料流建構函式](#vclrfinputfilestreamconstructorsanchor8)  
  
-   [輸入資料流建構函式](#vclrfinputstringstreamconstructorsanchor9)  
  
##  <a name="vclrfinputfilestreamconstructorsanchor8"></a> 輸入檔案資料流建構函式  
 有兩種方式可以建立輸入檔案資料流:  
  
-   使用 `void` 建構函式的引數，然後呼叫 `open` 成員函式:  
  
    ```  
    ifstream myFile; // On the stack  
    myFile.open( "filename" );  
  
    ifstream* pmyFile = new ifstream; // On the heap  
    pmyFile->open( "filename" );  
    ```  
  
-   指定文件以及旗標在建構函式引動過程，藉此開啟檔案在建構期間:  
  
    ```  
    ifstream myFile( "filename" );  
    ```  
  
##  <a name="vclrfinputstringstreamconstructorsanchor9"></a> 輸入資料流建構函式  
 輸入資料流建構函式需要預先配置的， preinitialized 儲存位址:  
  
```  
string s("123.45");  
double amt;  
istringstream myString( s );   
//istringstream myString( "123.45" ) also works  
myString >> amt; // amt contains 123.45  
```  
  
## 請參閱  
 [輸入資料流](../standard-library/input-streams.md)