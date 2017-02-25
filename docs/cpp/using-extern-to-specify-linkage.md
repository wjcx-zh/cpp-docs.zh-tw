---
title: "使用 extern 指定連結 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "extern"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "宣告, 外部"
  - "extern 關鍵字 [C++], 非 C++ 函式的連結"
  - "外部連結, extern 修飾詞"
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 使用 extern 指定連結
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
        extern string-literal { declaration-list }  
extern string-literal declaration  
```  
  
## 備註  
 `extern` 關鍵字可宣告變數或函式，並指定其具有外部連結 \(在已定義檔案之外的檔案中皆為可見\)。  修改變數時，`extern` 可指定變數的靜態持續期間 \(該變數會在程式啟動時配置，並在程式結束時解除配置\)。  變數或函式可能會在另一個原始程式檔中定義，或在相同的檔案中定義。  在檔案範圍上宣告的變數和函式預設為外部宣告。  
  
## 範例  
  
```  
// specifying_linkage1.cpp  
int i = 1;  
void other();  
  
int main() {  
   // Reference to i, defined above:  
   extern int i;  
}  
  
void other() {  
   // Address of global i assigned to pointer variable:  
   static int *external_i = &i;  
  
   // i will be redefined; global i no longer visible:  
   // int i = 16;  
}  
```  
  
 在 C\+\+ 中，透過字串使用時，`extern` 會將其他語言的連接慣例指定為供宣告子使用。  只有在先前宣告為具有 C 連結時，才可以存取 C 函式和資料。  不過，您必須在另行編譯的轉譯單位中定義它們。  
  
 Microsoft C\+\+ 在 **string\-literal** 欄位中支援字串 **"C"** 和 *"C\+\+"*。  所有使用 `extern` "C" 語法的標準 Include 檔都可在 C\+\+ 程式中使用執行階段程式庫函式。  
  
## 範例  
 下列範例顯示宣告具有 C 連結之名稱的替代方式：  
  
```  
// specifying_linkage2.cpp  
// compile with: /c  
// Declare printf with C linkage.  
extern "C" int printf( const char *fmt, ... );  
  
//  Cause everything in the specified header files  
//   to have C linkage.  
extern "C" {  
   // add your #include statements here  
   #include <stdio.h>  
}  
  
//  Declare the two functions ShowChar and GetChar  
//   with C linkage.  
extern "C" {  
   char ShowChar( char ch );  
   char GetChar( void );  
}  
  
//  Define the two functions ShowChar and GetChar  
//   with C linkage.  
extern "C" char ShowChar( char ch ) {  
   putchar( ch );  
   return ch;  
}  
  
extern "C" char GetChar( void ) {  
   char ch;  
  
   ch = getchar();  
   return ch;  
}  
  
// Declare a global variable, errno, with C linkage.  
extern "C" int errno;  
```  
  
 如果函式具有多個連結規格，這些規格必須一致；將函式宣告為同時具有 C 和 C\+\+ 連結是錯誤的。  此外，如果程式中的一個函式發生兩次宣告 \(一個使用連結規格，另一個沒有\)，則使用連結規格的宣告必須是第一個。  第一個宣告會針對任何已經有連結規格的其餘函式宣告指定連結。  例如:  
  
```  
extern "C" int CFunc1();  
...  
int CFunc1();            // Redeclaration is benign; C linkage is  
                         //  retained.  
  
int CFunc2();  
...  
extern "C" int CFunc2(); // Error: not the first declaration of  
                         //  CFunc2;  cannot contain linkage  
                         //  specifier.  
```  
  
 在複合連結指定名稱 \(**{ }**\) 本體內明確宣告為 **static** 的函式和物件均視為靜態函式或物件；會忽略連結指定名稱。  其他函式和物件的行為會就像使用 `extern` 關鍵字宣告一般   \(如需關於 [使用 extern 指定連結](../cpp/using-extern-to-specify-linkage.md)\) 關鍵字的詳細資訊，請參閱`extern`。  
  
## 請參閱  
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [\(NOTINBUILD\)Linkage Specifications](http://msdn.microsoft.com/zh-tw/d2b0cff1-7798-4c38-9ac8-61c3bfe2bfb9)   
 [extern 儲存類別規範](../c-language/extern-storage-class-specifier.md)   
 [識別項的行為](../c-language/behavior-of-identifiers.md)   
 [連結](../c-language/linkage.md)