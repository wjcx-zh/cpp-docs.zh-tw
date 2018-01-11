---
title: "Visual c + + 文件標籤的分隔符號 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: XML documentation, delimiters
ms.assetid: debfbdd9-63fa-4c58-a18e-a4d203d241d7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 134605f86ef8019d34f5246fd75abbbf94d40fbc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="delimiters-for-visual-c-documentation-tags"></a>Visual C++ 文件標記的分隔符號
文件標籤的使用需要分隔符號，這表示編譯器的文件註解開始及結束的位置。  
  
 您可以搭配使用下列類型的分隔符號與 XML 文件標記︰  
  
 `///`  
 這是文件範例所示，和 Visual c + + 專案範本所使用的表單。  
  
 `/** */`  
 這些是多行的分隔符號。  
  
 沒有使用格式化規則`/** */`分隔符號：  
  
-   包含列`/**`分隔符號，如果該行的其餘部分為泛空白字元，則不會處理註解。 如果第一個字元是空白字元，空白字元會被忽略，與處理其餘的列。 否則，會將 `/**` 分隔符號後面的整行文字處理為註解的一部分。  
  
-   包含的那一行的`*/`分隔符號，如果有最多是只有空白字元`*/`分隔符號，該行會被忽略。 否則，根據下列項目符號中所述的模式比對規則，會將到 `*/` 分隔符號為止的整行文字都處理為註解的一部分。  
  
-   之後的開頭行`/**`分隔符號，則編譯器會尋找常見的模式包含選擇性泛空白字元和星號每一行的開頭 (`*`)，後面接著選擇性更多的泛空白字元。 如果編譯器發現的每一行開頭的一組常用的字元，就會忽略所有的程式碼行之後, 該模式`/**`分隔符號，甚至可能包含的那一行`*/`分隔符號。  
  
 一些範例如下：  
  
-   下列註解中唯一會處理的部分是開頭為 `<summary>` 的那一行。 下列兩個標記格式會產生相同的註解：  
  
    ```  
    /**  
    <summary>text</summary>   
    */  
    /** <summary>text</summary> */  
    ```  
  
-   編譯器套用模式，"*"要略過第二個和第三個線條的開頭。  
  
    ```  
    /**  
     * <summary>  
     *  text </summary>*/  
    ```  
  
-   編譯器在這個註解中尋找任何模式，因為在第二行沒有任何星號。 因此，第二個和第三個線條上的所有文字向上到`*/`，將會處理做為註解的一部分。  
  
    ```  
    /**  
     * <summary>  
       text </summary>*/  
    ```  
  
-   編譯器在這個註解中尋找任何模式，原因有兩個。 首先，沒有列的開頭是星號前面的空格數一致。 其次，第五行的開頭是 Tab，這與空白字元不符。 因此，所有文字的第二行，直到從`*/`將註解的一部分處理。  
  
    ```  
    /**  
      * <summary>  
      * text   
     *  text2  
       *  </summary>  
    */  
    ```  
  
## <a name="see-also"></a>請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)