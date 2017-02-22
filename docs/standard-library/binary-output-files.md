---
title: "二進位輸出檔案 | Microsoft Docs"
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
  - "二進位資料, 二進位輸出檔案"
  - "檔案 [C++], 二進位輸出檔案"
  - "I/O [C++], 二進位輸出檔案"
ms.assetid: 180954af-8cd6-444b-9a76-2f630a3389d8
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 二進位輸出檔案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

資料流為文字最初設計，因此，預設輸出模式是文字。  在文字模式中，新行字元 \(十六、10\) 展開為 16 位元的重設為一組 \(僅限\)。  增益集可能會造成問題，如下所示:  
  
```  
// binary_output_files.cpp  
// compile with: /EHsc  
#include <fstream>  
using namespace std;  
int iarray[2] = { 99, 10 };  
int main( )  
{  
    ofstream os( "test.dat" );  
    os.write( (char *) iarray, sizeof( iarray ) );  
}  
```  
  
 您可能預期這個程式的輸出位元組序列{99， 0， 10， 0};相反地，它會輸出{99， 0， 13， 10， 0}，則會產生預期二進位編碼的程式的問題。  如果您需要 true 二進位輸出，您可以使用 [ofstream](../Topic/ofstream.md) 建構函式模式引數，字元會寫入未轉換，您可以指定二進位輸出:  
  
```  
// binary_output_files2.cpp  
// compile with: /EHsc  
#include <fstream>  
using namespace std;  
int iarray[2] = { 99, 10 };  
  
int main()  
{  
   ofstream ofs ( "test.dat", ios_base::binary );  
  
   // Exactly 8 bytes written  
   ofs.write( (char*)&iarray[0], sizeof(int)*2 );   
}  
```  
  
## 請參閱  
 [輸出資料流](../standard-library/output-streams.md)