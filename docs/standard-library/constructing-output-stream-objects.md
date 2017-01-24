---
title: "建構輸出資料流物件 | Microsoft Docs"
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
  - "輸出資料流物件"
ms.assetid: 93c8eab6-610c-4f48-b76d-1d960cac7641
caps.latest.revision: 9
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 建構輸出資料流物件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您只使用預先定義的 `cout`、 `cerr`或 `clog` 物件，您並不需要建構輸出資料流。  您必須使用建構函式為:  
  
-   [輸出檔案資料流建構函式](#vclrfoutputfilestreamconstructorsanchor1)  
  
-   [輸出資料流建構函式](#vclrfoutputstringstreamconstructorsanchor2)  
  
##  <a name="vclrfoutputfilestreamconstructorsanchor1"></a> 輸出檔案資料流建構函式  
 您可以用兩種方式來建構一個輸出檔資料流:  
  
-   使用預設建構函式，然後呼叫 `open` 成員函式。  
  
    ```  
    ofstream myFile; // Static or on the stack  
    myFile.open( "filename" );  
  
    ofstream* pmyFile = new ofstream; // On the heap  
    pmyFile->open( "filename" );  
    ```  
  
-   指定文件以及旗標在建構函式呼叫。  
  
    ```  
    ofstream myFile( "filename", ios_base::out);  
    ```  
  
##  <a name="vclrfoutputstringstreamconstructorsanchor2"></a> 輸出資料流建構函式  
 若要建構輸出資料流，您可以透過下列方式來使用 `ostringstream` :  
  
```  
   using namespace std;  
string sp;  
ostringstream myString;  
myString << "this is a test" << ends;  
sp = myString.str();  // Obtain string  
cout << sp < endl;   
```  
  
 `ends` 「操作工具加入必要的結束的 null 字元加入至字串。  
  
## 請參閱  
 [輸出資料流](../standard-library/output-streams.md)