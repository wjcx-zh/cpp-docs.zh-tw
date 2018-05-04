---
title: 使用 extern 指定連結 |Microsoft 文件
ms.custom: ''
ms.date: 04/06/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- extern
dev_langs:
- C++
helpviewer_keywords:
- extern keyword [C++], linkage to non-C++ functions
- declarations, external
- external linkage, extern modifier
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68bb5f35044a02b64c0475c7c94bc7a0b025cd3e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="using-extern-to-specify-linkage"></a>使用 extern 指定連結
## <a name="syntax"></a>語法  
  
```  
extern string-literal { declaration-list }  
extern string-literal declaration  
```  
  
## <a name="remarks"></a>備註  
 `extern` 關鍵字可宣告變數或函式，並指定其具有外部連結 (在已定義檔案之外的檔案中皆為可見)。 修改變數時，`extern` 可指定變數的靜態持續期間 (該變數會在程式啟動時配置，並在程式結束時解除配置)。 變數或函式可能會在另一個原始程式檔中定義，或在相同的檔案中定義。 在檔案範圍上宣告的變數和函式預設為外部宣告。  
  
## <a name="example"></a>範例  
  
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
  
 在 C++ 中，透過字串使用時，`extern` 會將其他語言的連接慣例指定為供宣告子使用。 只有在先前宣告為具有 C 連結時，才可以存取 C 函式和資料。 不過，您必須在另行編譯的轉譯單位中定義它們。  
  
 Microsoft c + + 支援字串 **"C"** 和 **"C + +"** 中*字串常值*欄位。 所有使用 `extern` "C" 語法的標準 Include 檔都可在 C++ 程式中使用執行階段程式庫函式。  
  
## <a name="example"></a>範例  
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
  
 如果函式具有多個連結規格，這些規格必須一致；將函式宣告為同時具有 C 和 C++ 連結是錯誤的。 此外，如果程式中的一個函式發生兩次宣告 (一個使用連結規格，另一個沒有)，則使用連結規格的宣告必須是第一個。 第一個宣告會針對任何已經有連結規格的其餘函式宣告指定連結。 例如:   
  
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
  
 函式和物件明確宣告為**靜態**複合連結指定名稱的主體內 (**{}**) 會被視為靜態函式或物件; 連結規範會被忽略。 其他函式和物件的行為會就像使用 `extern` 關鍵字宣告一般  (請參閱[使用 extern 指定連結](../cpp/using-extern-to-specify-linkage.md)如需詳細資訊`extern`關鍵字。)  
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../cpp/keywords-cpp.md)   
 [extern 儲存類別規範](../c-language/extern-storage-class-specifier.md)   
 [識別項的行為](../c-language/behavior-of-identifiers.md)   
 [連結](../c-language/linkage.md)