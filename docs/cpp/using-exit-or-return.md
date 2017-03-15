---
title: "結束 exit 或 return | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Exit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "exit 函式"
  - "return 關鍵字 [C++], 用於程式終止"
ms.assetid: b5136c5c-2505-4229-8691-2a1d6a98760b
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 結束 exit 或 return
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您呼叫 **exit** 或是從 **main** 執行 `return` 陳述式時，靜態物件會依照其初始化的反向順序終結。  下列範例將示範這類初始化和清除如何運作：  
  
## 範例  
  
```  
// using_exit_or_return1.cpp  
#include <stdio.h>  
class ShowData {  
public:  
   // Constructor opens a file.  
   ShowData( const char *szDev ) {  
   errno_t err;  
      err = fopen_s(&OutputDev, szDev, "w" );  
   }  
  
   // Destructor closes the file.  
   ~ShowData() { fclose( OutputDev ); }  
  
   // Disp function shows a string on the output device.  
   void Disp( char *szData ) {   
      fputs( szData, OutputDev );  
   }  
private:  
   FILE *OutputDev;  
};  
  
//  Define a static object of type ShowData. The output device  
//   selected is "CON" -- the standard output device.  
ShowData sd1 = "CON";  
  
//  Define another static object of type ShowData. The output  
//   is directed to a file called "HELLO.DAT"  
ShowData sd2 = "hello.dat";  
  
int main() {  
   sd1.Disp( "hello to default device\n" );  
   sd2.Disp( "hello to file hello.dat\n" );  
}  
```  
  
 在上述範例中，靜態物件 `sd1` 和 `sd2` 會在進入 `main` 之前建立並初始化。  使用 `return` 陳述式終止這個程式之後，第一個 `sd2` 就會終結，然後是 `sd1`。  `ShowData` 類別的解構函式會關閉與這些靜態物件相關聯的檔案 \(如需初始化、建構函式及解構函式的詳細資訊，請參閱[特殊成員函式](../misc/special-member-functions-cpp.md)\)。  
  
 另一種撰寫這個程式碼的方式，是使用區塊範圍宣告 `ShowData` 物件，讓物件能夠在超出範圍時終結：  
  
```  
int main() {  
   ShowData sd1, sd2( "hello.dat" );  
  
   sd1.Disp( "hello to default device\n" );  
   sd2.Disp( "hello to file hello.dat\n" );  
}  
```  
  
## 請參閱  
 [其他終止考量](../cpp/additional-termination-considerations.md)