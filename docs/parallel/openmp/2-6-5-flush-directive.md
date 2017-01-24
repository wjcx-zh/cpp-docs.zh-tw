---
title: "2.6.5 flush Directive | Microsoft Docs"
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
ms.assetid: a2ec5f74-9c37-424a-8376-47ab4a5829a2
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.6.5 flush Directive
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**排清**指示詞，無論是外顯或隱含的會指定"跨執行緒"序列點的實作，才能確保小組中的所有執行緒都具有一致 \(下述\) 在記憶體中特定物件的檢視。  這表示前一個評估的運算式參考這些物件都已完成，而且還沒有開始後續的評估。  例如，編譯器必須還原從暫存器物件的值到記憶體，而硬體可能需要清除記憶體的寫入緩衝區並重新載入記憶體中物件的值。  
  
 語法**排清**指示詞時，如下所示：  
  
```  
#pragma omp flush [(variable-list)]  new-line  
```  
  
 如果需要進行同步處理的物件所有被指定的變數，那麼這些變數可指定在選擇性的*變數清單*。  如果變數的指標出現在*變數清單*、 清除指標本身、 非物件指標參考。  
  
 A **排清** 指示詞，而不 *變數清單*自動存放工期與同步處理所有的共用物件，但無法存取的物件。  \(這是可能有更多的額外負荷，比**排清** 與 *變數清單*。\) A **排清** 指示詞，而不 *變數清單*隱含的下列指示詞：  
  
-   `barrier`  
  
-   在進入和離開**要徑**  
  
-   在進入和離開`ordered`  
  
-   在進入和離開**平行**  
  
-   在結束**的**  
  
-   在結束**區段**  
  
-   在結束**單一**  
  
-   在進入和離開**的平行**  
  
-   在進入和離開**平行的區段**  
  
 如果不表示該指示詞`nowait`子句會出現。  請注意， **排清**指示詞不會表示為下列其中一項：  
  
-   在進入**的**  
  
-   在進入或離開**母片**  
  
-   在進入**區段**  
  
-   在進入**單一**  
  
 存取的暫時性限定的型別物件值的參考就會當做有**排清**指示詞指定該物件在先前的序列點。  修改與靜態限定的型別物件的值的參考就會當做沒有**排清**指示詞指定該物件在後續的序列點。  
  
 請注意，因為**排清**指示詞並沒有 c 語言陳述式做為其語法的一部分，有一些限制，在程式中的位置上。  請參閱 [＜ 附錄 c](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md) 的正式的文法。  下列範例會示範這些限制。  
  
```  
/* ERROR - The flush directive cannot be the immediate  
*          substatement of an if statement.  
*/  
if (x!=0)  
   #pragma omp flush (x)  
...  
  
/* OK - The flush directive is enclosed in a  
*      compound statement  
*/  
if (x!=0) {  
   #pragma omp flush (x)  
}  
```  
  
 若要限制**排清**指示詞如下：  
  
-   在指定的變數**排清**指示詞不可以有參考型別。