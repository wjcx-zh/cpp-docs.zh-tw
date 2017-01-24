---
title: "basic_ofstream 類別 | Microsoft Docs"
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
  - "std::basic_ofstream"
  - "basic_ofstream"
  - "std.basic_ofstream"
  - "fstream/std::basic_ofstream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_ofstream 類別"
ms.assetid: 3bcc9c51-6dfc-4844-8fcc-22ef57c9dff1
caps.latest.revision: 24
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# basic_ofstream 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述一個物件，該物件可控制將項目和編碼物件插入 [basic\_filebuf](../standard-library/basic-filebuf-class.md)\<`Elem`, `Tr`\> 類別的資料流緩衝區，搭配 `Elem` 類型的項目，而且其字元特性是由 `Tr` 類別所決定。  
  
## 語法  
  
```  
template <class Elem, class Tr = char_traits<Elem> >  
    class basic_ofstream : public basic_ostream<Elem, Tr>  
```  
  
#### 參數  
 `Elem`  
 檔案緩衝區的基本項目。  
  
 `Tr`  
 緩衝區基本項目的特性 \(通常 `char_traits`\<`Elem`\>\)。  
  
## 備註  
 當 `basic_ofstream` 的 `wchar_t` 特製化寫入檔案時，如果該檔案在文字模式中開啟，則它會寫入 MBCS 序列。  此內部表示法將使用 `wchar_t` 字元的緩衝區。  
  
 此物件會儲存類別 `basic_filebuf`\<`Elem`, `Tr`\> 的物件。  
  
## 範例  
 下列範例會示範如何建立 `basic_ofstream` 物件並寫入文字。  
  
```  
// basic_ofstream_class.cpp  
// compile with: /EHsc  
#include <fstream>  
  
using namespace std;  
  
int main(int argc, char **argv)  
{  
    ofstream ofs("ofstream.txt");  
    if (!ofs.bad())  
    {  
        ofs << "Writing to a basic_ofstream object..." << endl;  
        ofs.close();  
    }  
}  
```  
  
### 建構函式  
  
|||  
|-|-|  
|[basic\_ofstream](../Topic/basic_ofstream::basic_ofstream.md)|建立 `basic_ofstream` 類型的物件。|  
  
### 成員函式  
  
|||  
|-|-|  
|[關閉](../Topic/basic_ofstream::close.md)|關閉檔案。|  
|[is\_open](../Topic/basic_ofstream::is_open.md)|判斷檔案是否為開啟。|  
|[開啟](../Topic/basic_ofstream::open.md)|開啟檔案。|  
|[rdbuf](../Topic/basic_ofstream::rdbuf.md)|傳回預存資料流緩衝區的位址。|  
|[交換](../Topic/basic_ofstream::swap.md)|將這個 `basic_ofstream` 的內容和提供的 `basic_ofstream` 內容交換。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\=](../Topic/basic_ofstream::operator=.md)|指派此資料流物件的內容。  這是一個移動指派，包含不會留下複本的 `rvalue reference`。|  
  
## 需求  
 **標頭：**\<fstream\>  
  
 **命名空間:** std  
  
## 請參閱  
 [basic\_ostream 類別](../standard-library/basic-ostream-class.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)