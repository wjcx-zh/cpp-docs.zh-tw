---
title: "編輯樣式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ES_READONLY"
  - "ES_WANTRETURN"
  - "ES_UPPERCASE"
  - "ES_NUMBER"
  - "ES_AUTOHSCROLL"
  - "ES_LOWERCASE"
  - "ES_RIGHT"
  - "ES_MULTILINE"
  - "ES_PASSWORD"
  - "ES_NOHIDESEL"
  - "ES_OEMCONVERT"
  - "ES_LEFT"
  - "ES_CENTER"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "編輯樣式 [MFC]"
  - "ES_AUTOHSCROLL 常數"
  - "ES_AUTOVSCROLL 常數"
  - "ES_CENTER 常數"
  - "ES_LEFT 常數"
  - "ES_LOWERCASE 常數"
  - "ES_MULTILINE 常數"
  - "ES_NOHIDESEL 常數"
  - "ES_NUMBER 常數"
  - "ES_OEMCONVERT 常數"
  - "ES_PASSWORD 常數"
  - "ES_READONLY 常數"
  - "ES_RIGHT 常數"
  - "ES_UPPERCASE 常數"
  - "ES_WANTRETURN 常數"
ms.assetid: e6291dd6-f2cb-4ce2-ac31-32272526625c
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# 編輯樣式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

-   **ES\_AUTOHSCROLL** 自動移動文字向右捲動 10 個字元，當使用者輸入字元位於行的結尾。  當使用者按下 ENTER 鍵時，控制項將所有文字回到位置 0。  
  
-   當使用者在最後一行時，會進入**ES\_AUTOVSCROLL** 自動移動一頁的文字。  
  
-   **ES\_CENTER** 集中在單行或多行編輯控制項的文字。  
  
-   **ES\_LEFT** 靠左對齊單行或多行編輯控制項的文字。  
  
-   會將輸入至編輯控制項，**ES\_LOWERCASE** 所有的字元轉換成小寫。  
  
-   **ES\_MULTILINE** 將多行編輯控制項。\(預設值為單一行\)。如果 **ES\_AUTOVSCROLL** 樣式指定，編輯控制項垂直顯示多行做為可能和捲動，當使用者按下 ENTER 鍵時。  如果未指定 **ES\_AUTOVSCROLL** ，編輯控制項中顯示多行做為可能和嗶聲，如果輸入時，在沒有其他行不會顯示時。  如果 **ES\_AUTOHSCROLL** 樣式指定，多行編輯控制項自動向水平方向捲動時插入號超過控制項右邊緣時。  若要開始新的一行，使用者必須按 Enter。  如果未指定 **ES\_AUTOHSCROLL** ，控制項會自動將文字換行到下一行的開頭，則需要;，如果輸入時，新行也起始。  視窗大小是由自動換行的位置。  如果視窗大小變更時，自動換行位置變更，則文字會重新顯示。  多行編輯控制項可以擁有捲軸。  有捲軸的編輯控制項處理它的捲動列訊息。  沒有捲軸的編輯控制項如上所述移動及處理父視窗傳送的所有捲動資訊。  
  
-   **ES\_NOHIDESEL** 正常，編輯控制項隱藏選取範圍，當控制項失去輸入焦點且反轉選取範圍，當控制項收到輸入焦點時。  指定 **ES\_NOHIDESEL** 刪除此預設動作。  
  
-   **ES\_NUMBER** 只允許數字輸入至編輯控制項。  
  
-   在編輯控制項中輸入的文字從**ES\_OEMCONVERT** ANSI 字元集轉換成 OEM 字元集然後回到 ANSI。  當應用程式呼叫 Windows 函式 `AnsiToOem` 轉換在編輯控制項的 ANSI 字串到 OEM 字元時，這可確保適當的字元轉換。  這個樣式為包含檔案名稱的編輯控制項是最有用的。  
  
-   **ES\_PASSWORD** 顯示所有字元，星號 \(**\***\)，則會將輸入至編輯控制項。  應用程式可以使用 `SetPasswordChar` 成員函式來變更顯示的字元。  
  
-   **ES\_READONLY** 防止使用者輸入或編輯在編輯控制項的文字。  
  
-   **ES\_RIGHT** 靠右對齊在單行或多行編輯控制項的文字。  
  
-   會將輸入至編輯控制項，**ES\_UPPERCASE** 所有的字元轉換成大寫。  
  
-   **ES\_WANTRETURN** 指定插入歸位字元，當使用者按下 ENTER 鍵時，輸入文字至對話方塊中多行編輯控制項。  沒有這個模式，按 ENTER 鍵與按鈕對話 boxs 預設按鈕的作用。  這個樣式對單行編輯控制項沒有任何影響。  
  
## 請參閱  
 [MFC 使用的樣式](../../mfc/reference/styles-used-by-mfc.md)   
 [CEdit::Create](../Topic/CEdit::Create.md)   
 [Edit Control Styles](http://msdn.microsoft.com/library/windows/desktop/bb775464)