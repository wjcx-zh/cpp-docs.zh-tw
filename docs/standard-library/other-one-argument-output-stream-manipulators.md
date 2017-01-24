---
title: "其他單一引數輸出資料流操作工具 | Microsoft Docs"
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
  - "輸出資料流, 單一引數操作工具"
ms.assetid: e381dee8-6b16-4cef-805a-4a6a1d2b696b
caps.latest.revision: 11
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 其他單一引數輸出資料流操作工具
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列範例會使用類別， `money`是 `long` 型別。  `setpic` 操作工具附加格式圖片」字串可由類別使用 `money`的資料流插入運算子的類別。  因為資料流類別的資料成員，因此，您不需要從衍生新的輸出資料流類別，圖像字串會儲存為靜態變數在 `money` 類別而不是。  
  
## 範例  
  
```  
// one_arg_output.cpp  
// compile with: /GR /EHsc  
#include <iostream>  
#include <iomanip>  
#include <string>  
using namespace std;  
  
typedef char* charp;  
  
class money   
{  
private:  
    long value;  
    static char *szCurrentPic;  
public:  
    money( long val ) { value = val; }  
    friend ostream& operator << ( ostream& os, money m ) {  
        // A more complete function would merge the picture  
        // with the value rather than simply appending it  
        os << m.value << '[' << money::szCurrentPic << ']';  
        return os;  
    }  
    static void setpic( char* szPic ) {  
        money::szCurrentPic = new char[strlen( szPic ) + 1];  
        strcpy_s( money::szCurrentPic, strlen( szPic ) + 1, szPic );  
    }  
};  
  
char *money::szCurrentPic;  // Static pointer to picture  
  
void fb( ios_base& os, char * somename )  
{  
   money::setpic(somename);  
/*  
   ostream *pos = dynamic_cast<ostream*>(&os);  
   if (pos)  
   {  
      for( int i=0; i < l; i++ )  
      (*pos) << ' ';  
   };  
*/  
}  
  
_Smanip<charp>  
   __cdecl setpic(char * somename)  
   {     
   return (_Smanip<charp>(&fb, somename));  
   }  
  
int main( )  
{  
    money amt = (long)35235.22;  
    cout << setiosflags( ios::fixed );  
    cout << setpic( "###,###,###.##" ) << "amount = " << amt << endl;  
}  
```  
  
## 請參閱  
 [具有引數的自訂操作工具](../standard-library/custom-manipulators-with-arguments.md)