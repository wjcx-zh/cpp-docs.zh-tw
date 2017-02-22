---
title: "C 位元欄位 | Microsoft Docs"
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
  - "位元欄位"
  - "bitfields"
ms.assetid: 9faf74c4-7fd5-4b44-ad18-04485193d06e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# C 位元欄位
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

除了結構或等位的成員宣告子之外，結構宣告子也可以是指定的位元數，稱為位元欄位 \(Bit Field\)」它的長度從欄位名稱的宣告子產生以冒號分隔。  位元欄位會解譯成整數類資料型別。  
  
## 語法  
 *結構宣告子*:  
 *宣告子*  
  
 *型別規範宣告子*  選取               **:**  *常數運算式*  
  
 *常數運算式* 以位元組指定欄位的寬度。  *型別指定名稱* 對 `declarator` 的型別規範必須是 `unsigned int`、  **帶正負號的整數** ，則為 `int`，而且 *常數運算* 式必須是非負數的整數值。  如果值為零，宣告沒有 `declarator`。  傳回位元欄位的位元欄位、指標位元欄位和函式不允許。  選擇性 `declarator` 命名位元欄位。  位元欄位只能宣告為結構的一部分。  傳址運算子 \(**&**\) 無法套用的位元欄位元件。  
  
 未命名的位元欄位無法參考，因此，它們在執行階段的內容無法預期。  它們可以為對齊目的而被當做「錯誤」的欄位。  指定寬度為 0 的未命名的位元欄位以確保遵循它在 *結構宣告清單之成員的* 儲存在 `int` 界限開始。  
  
 位元欄位必須夠長以包含這個位元。  例如，這兩個陳述式不是合法的:  
  
```  
short a:17;        /* Illegal! */  
int long y:33;     /* Illegal! */  
```  
  
 這個範例會定義名為的二維陣列的結構的具名 `screen`。  
  
```  
struct   
{  
    unsigned short icon : 8;  
    unsigned short color : 4;  
    unsigned short underline : 1;  
    unsigned short blink : 1;  
} screen[25][80];  
```  
  
 包含 2000 個元素的陣列。  每個項目都是包含四個位元欄位成員的個別結構: `icon`、 `color`、 `underline`和 `blink`。  每個結構的大小是兩個位元組。  
  
 位元欄位的語意與整數型別相同。  這表示無論欄位有多少位元組，位元欄位用都會與相同基底類型會使用的表示方法。  
  
 **Microsoft 專有的**  
  
 為 `int` 定義的位元欄位會分正負號。  對 ANSI C 標準的 Microsoft 擴充功能允許 `char` 和 **long** 型別 \( **signed** \) 和 `unsigned`位元欄位。  具有基底型別的 **long**、 **short**或**signed** `char` \(或 `unsigned`\) 強制對齊未命名的位元欄位的界限所適用的基底型別。  
  
 位元欄位在整數中配置從最小顯著性到最有效的位元。  下列程式碼中。  
  
```  
struct mybitfields  
{  
    unsigned short a : 4;  
    unsigned short b : 5;  
    unsigned short c : 7;  
} test;  
  
int main( void );  
{  
    test.a = 2;  
    test.b = 31;  
    test.c = 0;  
}  
```  
  
 將位元安排如下:  
  
```  
00000001 11110010  
cccccccb bbbbaaaa  
```  
  
 因為處理器的 8086 系列在高位元組之前儲存低位元組的整數值，整數上面的 `0x01F2` 在實體記憶體將會儲存為 `0xF2` 中 `0x01`後面。  
  
 **END Microsoft 專有**  
  
## 請參閱  
 [結構宣告](../c-language/structure-declarations.md)