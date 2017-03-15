---
title: "HTML 的基本概念 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "HTML, 關於 HTML"
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# HTML 的基本概念
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

大部分的瀏覽器有檢查您瀏覽網頁的 HTML 原始檔的功能。  當您檢視原始碼，您會看到一些 HTML \(超文字標記語言\) 的標記，周圍以角括弧 \(\<\>\) 包圍，其中為文字。  
  
 下方的步驟使用 HTML 標記建立簡單的 Web 網頁。  在下列步驟中，您將輸入純文字到記事本的檔案，進行一些變更，儲存檔案，並重新載入至您的瀏覽器中的網頁來查看您的變更。  
  
#### 若要建立 HTML 檔  
  
1.  開啟記事本或任何純文字編輯器。  
  
2.  從 \[**檔案**\] 功能表選擇 \[`New`\]。  
  
3.  輸入下列行：  
  
    ```  
    <HTML>  
    <HEAD>  
    <TITLE>Top HTML Tags</TITLE>  
    </HEAD>  
    </HTML>  
    ```  
  
4.  從 **檔案** 功能表上，選擇 \[**儲存**\]，然後將檔案另存為 c:\\webpages\\First.htm。  讓檔案在編輯器保持開啟。  
  
5.  轉換為您的瀏覽器，並從 **檔案** 功能表上，選取 **開啟** 或在瀏覽器的 URL 編輯方塊打上 `file://C:/webpages/first.htm`。  您應該會看到空白網頁與視窗的標題「Top HTML Tags」。  
  
     請注意標記在角括弧組中。  標記不區分大小寫，不過，大小寫通常用做標記使引人注意。  
  
     標記 \<HTML\> 開始文件，並且 \<\/HTML\> 結束它。  結束標記 \(不一定需要\) 與開始標記相似，不過，有一個正斜線 \(\/\) 在標記之前。  不應該在角括弧 \(\<\) 和您的標記之間保留空白。  
  
6.  切換回記事本，並在 \<\/HEAD\> 下一行，請輸入:  
  
    ```  
    <BODY>  
    HTML is swell.  
    Life is good.  
    </BODY>  
    ```  
  
7.  從 \[**檔案**\] 功能表中，選擇 \[**儲存** \]。  
  
8.  切換回您的瀏覽器並重新整理頁面。  
  
     文字會出現在您的瀏覽器視窗工作區。  請注意您的歸位字元會被忽略。  如果您想要有分行符號，您必須包括 `<BR>` 標記，在第一行之後。  
  
     對於後面的所有步驟，在 \<BODY\> 和 \<\/BODY\> 之間的任何位置插入文字以加入您的文件主體。  
  
9. 加入標題:  
  
    ```  
    <H3>Here's the big picture</H3>  
    ```  
  
10. 加入影像，使用儲存於和您的頁面相同目錄的 .gif 檔案:  
  
    ```  
    <IMG src="yourfile.gif">  
    ```  
  
11. 加入清單:  
  
    ```  
    <UL>Make me an unordered list.  
    <LI>One programmer</LI>  
    <LI>Ten SDKs</LI>  
    <LI>Great Internet Apps</LI>  
    </UL>  
    ```  
  
12. 若要編號清單，請在 \<UL\> 和 \<\/UL\> 標記位置使用成對的 \<OL\> 和 \<\/OL\> 標記。  
  
 這可讓您啟動。  如果您發現網頁的強大功能，您可以藉由檢查 HTML 來源找到如何建立。  HTML 編輯器如 Microsoft Front Page 可用來建立簡單和進階的頁面。  
  
 這是您建立之檔案的完整 HTML 原始檔:  
  
```  
<HTML>  
<HEAD>  
<TITLE>Top HTML Tags</TITLE>  
</HEAD>  
<BODY>  
HTML is swell.<BR>  
Life is good.  
<H3>Here's the big picture</H3>  
<IMG src="yourfile.gif">  
<UL>Make me an unordered list.  
<LI>One programmer</LI>  
<LI>Ten SDKs</LI>  
<LI>Great Internet Apps</LI>  
</UL>  
</BODY>  
</HTML>  
```  
  
 對於標記的完整描述，屬性和副檔名，請參閱超文字標記語言 \(HTML\) 規格:  
  
 [http:\/\/www.w3.org\/pub\/WWW\/MarkUp\/](http://www.w3.org/pub/WWW/MarkUp/)  
  
## 請參閱  
 [MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)