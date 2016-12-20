---
title: "Visual C++ 文件標記的分隔符號 | Microsoft Docs"
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
  - "XML 文件, 分隔符號"
ms.assetid: debfbdd9-63fa-4c58-a18e-a4d203d241d7
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Visual C++ 文件標記的分隔符號
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用資料標記需要符號，指示編譯器文件註解開始處開始和結束。  
  
 您可以使用下列幾種分隔符號，以搭配 XML 文件標記使用：  
  
 `///`  
 這是在文件範例顯示和 Visual C\+\+ 專案範本使用的表單。  
  
 `/** */`  
 這些是多行的符號。  
  
 有一些格式化規則，當使用 `/** */` 符號時:  
  
-   包含 `/**`分隔符號的程式碼行，則為，如果程式碼行的其餘部分是空白字元，線條沒有為註解處理。  如果第一個字元是泛空白字元，該泛空白字元會被忽略，而且一行的其餘部分處理。  否則，在 `/**` 分隔符號之後的所有內容，都會當做註解的一部分來處理。  
  
-   包含 `*/`符號的線條，則為，如果只有空白字元由 `*/` 符號決策，行被忽略。  否則，在 `*/` 分隔符號之前，程式碼行的文字將會當做註解的一部分來處理，並受制於下列項目符號中所描述的模式比對規則。  
  
-   指定線條，從 `/**` 符號後開始，則編譯器會包含選擇性泛空白字元和星號的每一行開頭尋找一般模式 \(`*`\)，再加上更選擇性泛空白字元。  如果編譯器尋找通用字元在每一行的開頭，它在 `/**` 符號之後將忽略所有行的該模式，而且可以包含 `*/` 分隔符號的程式碼行。  
  
 以下是部分範例：  
  
-   下列註解中唯一會進行處理的部分，是以 `<summary>` 開頭的那行程式碼。  下列兩個標記格式會產生相同的註解:  
  
    ```  
    /**  
    <summary>text</summary>   
    */  
    /** <summary>text</summary> */  
    ```  
  
-   編譯器將樣式「\*」在第二和第三行首忽略。  
  
    ```  
    /**  
     * <summary>  
     *  text </summary>*/  
    ```  
  
-   因為在第二行中，星號編譯器不會出現在此註解的樣式。  因此，當做註解的一部分，在第二和第三行的所有文字，直到 `*/`，處理。  
  
    ```  
    /**  
     * <summary>  
       text </summary>*/  
    ```  
  
-   編譯器原因有兩個不會出現在此註解的樣式。  首先，沒有從空間統一的一個星號之前的行。  其次，第五行程式碼以標籤做為開頭，與空白字元不相符。  因此，當做註解的一部分，從第二行中的所有文字直到 `*/` 處理。  
  
    ```  
    /**  
      * <summary>  
      * text   
     *  text2  
       *  </summary>  
    */  
    ```  
  
## 請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)