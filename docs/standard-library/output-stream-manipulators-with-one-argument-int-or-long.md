---
title: "具有單一引數 (int 或 long) 的輸出資料流操作工具 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- output streams, int or long argument manipulators
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 06336b580976ea3ad26f0acb34956f4243f4325d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="output-stream-manipulators-with-one-argument-int-or-long"></a>具有單一引數 (int 或 long) 的輸出資料流操作工具
iostream 類別程式庫提供一組巨集，可用來建立參數化的操作工具。 具有單一 `int` 或 `long` 引數的操作工具是特殊案例。 若要建立可接受單一 `int` 或 `long` 引數 (例如 `setw`) 的操作工具，您必須使用定義於 \<iomanip> 中的 _Smanip 巨集。 本範例定義 `fillblank` 操作工具，它會將指定的空格數目插入資料流中：  
  
## <a name="example"></a>範例  
  
```cpp  
// output_stream_manip.cpp  
// compile with: /GR /EHsc  
#include <iostream>  
#include <iomanip>  
using namespace std;  
  
void fb( ios_base& os, int l )  
{  
   ostream *pos = dynamic_cast<ostream*>(&os);  
   if (pos)  
   {  
      for( int i=0; i < l; i++ )  
      (*pos) << ' ';  
   };  
}  
  
_Smanip<int>  
   __cdecl fillblank(int no)  
   {     
   return (_Smanip<int>(&fb, no));  
   }  
  
int main( )  
{  
   cout << "10 blanks follow" << fillblank( 10 ) << ".\n";  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [具有引數的自訂操作工具](../standard-library/custom-manipulators-with-arguments.md)

