---
title: "二進位輸出檔案 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- I/O [C++], binary output files
- files [C++], binary output files
- binary data, binary output files
ms.assetid: 180954af-8cd6-444b-9a76-2f630a3389d8
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: da2d0ac01919773492f075f2e2dd6a7d210224fb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="binary-output-files"></a>二進位輸出檔案
資料流最初是針對文字所設計，因此預設輸出模式是文字。 在文字模式下，新行字元 (十六進位 10) 會展開以復-換行 （僅限 16 位元）。 此擴充可能造成問題，如下所示：  
  
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
  
 您可能預期此程式輸出位元組序列 { 99, 0, 10, 0 }，但它卻輸出 { 99, 0, 13, 10, 0 }，導致預期二進位輸入的程式出現問題。 如果您需要精確的二進位輸出 (其中的字元會在未轉譯的情況下寫入)，您可以藉由使用 [ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream) 建構函式的 openmode 引數指定二進位輸出：  
  
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
  
## <a name="see-also"></a>另請參閱  
 [輸出資料流](../standard-library/output-streams.md)

