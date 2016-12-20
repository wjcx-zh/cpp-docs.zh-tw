---
title: "basic_fstream 類別 | Microsoft Docs"
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
  - "std::basic_fstream"
  - "basic_fstream"
  - "fstream/std::basic_fstream"
  - "std.basic_fstream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_fstream 類別"
ms.assetid: 8473817e-42a4-430b-82b8-b476c86bcf8a
caps.latest.revision: 24
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# basic_fstream 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述一個物件，該物件可控制使用 [basic\_filebuf](../standard-library/basic-filebuf-class.md)\<`Elem`, `Tr`\> 類別的資料流緩衝區插入及擷取項目和編碼物件、具有 `Elem` 類型的項目，而且其字元特性是由 `Tr` 類別所決定。  
  
## 語法  
  
```  
template <class Elem, class Tr = char_traits<Elem> >  
    class basic_fstream : public basic_iostream<Elem, Tr>  
```  
  
#### 參數  
 `Elem`  
 檔案緩衝區的基本項目。  
  
 `Tr`  
 緩衝區基本項目的特性 \(通常 `char_traits`\<`Elem`\>\)。  
  
## 備註  
 這個物件會儲存 `basic_filebuf`\<`Elem`, `Tr`\> 類別的物件。  
  
> [!NOTE]
>  fstream 物件的 get 指標和 put 指標彼此**相依**。  如果 get 指標移動，put 指標也會跟著移動。  
  
## 範例  
 下列範例示範如何建立可從中讀取和寫入的 `basic_fstream` 物件。  
  
```  
// basic_fstream_class.cpp  
// compile with: /EHsc  
  
#include <fstream>  
#include <iostream>  
  
using namespace std;  
  
int main(int argc, char **argv)  
{  
    fstream fs("fstream.txt", ios::in | ios::out | ios::trunc);  
    if (!fs.bad())  
    {  
        // Write to the file.  
        fs << "Writing to a basic_fstream object..." << endl;  
        fs.close();  
  
        // Dump the contents of the file to cout.  
        fs.open("fstream.txt", ios::in);  
        cout << fs.rdbuf();  
        fs.close();  
    }  
}  
```  
  
  **Writing to a basic\_fstream object...**   
### 建構函式  
  
|||  
|-|-|  
|[basic\_fstream](../Topic/basic_fstream::basic_fstream.md)|建構類型 `basic_fstream` 的物件。|  
  
### 成員函式  
  
|||  
|-|-|  
|[關閉](../Topic/basic_fstream::close.md)|關閉檔案。|  
|[is\_open](../Topic/basic_fstream::is_open.md)|判斷檔案是否為開啟。|  
|[開啟](../Topic/basic_fstream::open.md)|開啟檔案。|  
|[rdbuf](../Topic/basic_fstream::rdbuf.md)|將類型指標之預存資料流緩衝區的位址傳回至 [basic\_filebuf](../standard-library/basic-filebuf-class.md)\<`Elem`, `Tr`\>。|  
|[交換](../Topic/basic_fstream::swap.md)|將這個物件的內容與另一個 `basic_fstream` 物件的內容交換。|  
  
## 需求  
 **標頭：**\<fstream\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)