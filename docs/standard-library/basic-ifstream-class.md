---
title: "basic_ifstream 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "basic_ifstream"
  - "fstream/std::basic_ifstream"
  - "std::basic_ifstream"
  - "std.basic_ifstream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_ifstream 類別"
ms.assetid: 366cd9a7-efc4-4b7f-ba10-c8271e47ffcf
caps.latest.revision: 23
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# basic_ifstream 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述一個物件，該物件可控制來自 [basic\_filebuf](../standard-library/basic-filebuf-class.md)\<`Elem`, `Tr`\> 類別的資料流緩衝區擷取項目和編碼物件，搭配 `Elem` 類型的項目，而且其字元特性是由 `Tr` 類別所決定。  
  
## 語法  
  
```  
template <class Elem, class Tr = char_traits<Elem> >  
    class basic_ifstream : public basic_istream<Elem, Tr>  
```  
  
#### 參數  
 `Elem`  
 檔案緩衝區的基本項目。  
  
 `Tr`  
 緩衝區基本項目的特性 \(通常 `char_traits`\<`Elem`\>\)。  
  
## 備註  
 此物件會儲存類別 `basic_filebuf`\<`Elem`, `Tr`\> 的物件。  
  
## 範例  
 下列範例示範如何在檔案的文字中讀取。  
  
```  
// basic_ifstream_class.cpp  
// compile with: /EHsc  
  
#include <fstream>  
#include <iostream>  
  
using namespace std;  
  
int main(int argc, char **argv)  
{  
    ifstream ifs("basic_ifstream_class.txt");  
    if (!ifs.bad())  
    {  
        // Dump the contents of the file to cout.  
        cout << ifs.rdbuf();  
        ifs.close();  
    }  
}  
```  
  
## 輸入：basic\_ifstream\_class.txt  
  
```  
This is the contents of basic_ifstream_class.txt.  
```  
  
## 輸出  
  
```  
This is the contents of basic_ifstream_class.txt.  
```  
  
### 建構函式  
  
|||  
|-|-|  
|[basic\_ifstream](../Topic/basic_ifstream::basic_ifstream.md)|初始化 `basic_ifstream` 物件的新執行個體。|  
  
### 成員函式  
  
|||  
|-|-|  
|[關閉](../Topic/basic_ifstream::close.md)|關閉檔案。|  
|[is\_open](../Topic/basic_ifstream::is_open.md)|判斷檔案是否為開啟。|  
|[開啟](../Topic/basic_ifstream::open.md)|開啟檔案。|  
|[rdbuf](../Topic/basic_ifstream::rdbuf.md)|傳回預存資料流緩衝區的位址。|  
|[交換](../Topic/basic_ifstream::swap.md)|將此 `basic_ifstream` 的內容和提供的 `basic_ifstream` 內容交換。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\=](../Topic/basic_ifstream::operator=.md)|指派此資料流物件的內容。  這是一個移動指派，涉及不會留下複本的 `rvalue`。|  
  
## 需求  
 **標頭：**\<fstream\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)