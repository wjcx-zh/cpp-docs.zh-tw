---
title: "basic_filebuf 類別 | Microsoft Docs"
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
  - "std.basic_filebuf"
  - "fstream/std::basic_filebuf"
  - "std::basic_filebuf"
  - "basic_filebuf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_filebuf 類別"
ms.assetid: 3196ba5c-bf38-41bd-9a95-70323ddfca1a
caps.latest.revision: 24
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# basic_filebuf 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述資料流緩衝區，其控制類型 `Elem` 的項目 \(其字元特性由類別 `Tr` 所決定\)，與外部檔案中儲存的項目序列之間的往來傳輸。  
  
## 語法  
  
```  
template <class Elem, class Tr = char_traits<Elem> >  
    class basic_filebuf : public basic_streambuf<Elem, Tr>  
```  
  
#### 參數  
 `Elem`  
 檔案緩衝區的基本項目。  
  
 `Tr`  
 緩衝區基本項目的特性 \(通常 `char_traits`\<`Elem`\>\)。  
  
## 備註  
 範本類別描述資料流緩衝區，其控制類型 `Elem` 的項目 \(其字元特性由類別 `Tr` 所決定\)，與外部檔案中儲存的項目序列之間的往來傳輸。  
  
> [!NOTE]
>  類型 `basic_filebuf` 的物件是在類型 `char *` 的內部緩衝區內建立，不論類型參數 `Elem` 所指定的 `char_type`。  這表示在寫入內部緩衝區之前，Unicode 字串 \(包含 `wchar_t` 字元\) 會轉換為 ANSI 字串 \(包含 `char` 字元\)。  若要在緩衝區中儲存 Unicode 字串，請建立類型 `wchar_t` 的新緩衝區，並使用 [basic\_streambuf::pubsetbuf](../Topic/basic_streambuf::pubsetbuf.md)`()` 方法來設定它。  若要查看示範此行為的範例，請參閱以下範例。  
  
 類別 `basic_filebuf`\<`Elem`、`Tr`\> 的物件會儲存檔案指標，檔案指標會指定 `FILE` 物件，控制與開啟的檔案相關聯的資料流。  它也會將指標儲存至兩個檔案轉換 Facet，讓受保護的成員函式[溢位](../Topic/basic_filebuf::overflow.md)和[反向溢位](../Topic/basic_filebuf::underflow.md)使用。  如需詳細資訊，請參閱 [basic\_filebuf::open](../Topic/basic_filebuf::open.md)。  
  
## 範例  
 下列範例示範如何強制類型 `basic_filebuf<wchar_t>` 的物件，以藉由呼叫 `pubsetbuf()` 方法，在其內部緩衝區中儲存 Unicode 字元。  
  
```  
// unicode_basic_filebuf.cpp  
// compile with: /EHsc  
  
#include <iostream>  
#include <string>  
#include <fstream>  
#include <iomanip>  
#include <memory.h>  
#include <string.h>  
  
#define IBUFSIZE 16  
  
using namespace std;  
  
void hexdump(const string& filename);  
  
int main()  
{  
    wchar_t* wszHello = L"Hello World";  
    wchar_t wBuffer[128];  
  
    basic_filebuf<wchar_t> wOutFile;  
  
    // Open a file, wcHello.txt, then write to it, then dump the  
    // file's contents in hex  
    wOutFile.open("wcHello.txt",  
        ios_base::out | ios_base::trunc | ios_base::binary);  
    if(!wOutFile.is_open())  
    {  
        cout << "Error Opening wcHello.txt\n";  
        return -1;  
    }  
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));  
    wOutFile.close();  
    cout << "Hex Dump of wcHello.txt - note that output is ANSI chars:\n";  
    hexdump(string("wcHello.txt"));  
  
    // Open a file, wwHello.txt, then set the internal buffer of  
    // the basic_filebuf object to be of type wchar_t, then write  
    // to the file and dump the file's contents in hex  
    wOutFile.open("wwHello.txt",  
        ios_base::out | ios_base::trunc | ios_base::binary);  
    if(!wOutFile.is_open())  
    {  
        cout << "Error Opening wwHello.txt\n";  
        return -1;  
    }  
    wOutFile.pubsetbuf(wBuffer, (streamsize)128);  
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));  
    wOutFile.close();  
    cout << "\nHex Dump of wwHello.txt - note that output is wchar_t chars:\n";  
    hexdump(string("wwHello.txt"));  
  
    return 0;  
}  
  
// dump contents of filename to stdout in hex  
void hexdump(const string& filename)  
{  
    fstream ifile(filename.c_str(),  
        ios_base::in | ios_base::binary);  
    char *ibuff = new char[IBUFSIZE];  
    char *obuff = new char[(IBUFSIZE*2)+1];  
    int i;  
  
    if(!ifile.is_open())  
    {  
        cout << "Cannot Open " << filename.c_str()  
             << " for reading\n";  
        return;  
    }  
    if(!ibuff || !obuff)  
    {  
        cout << "Cannot Allocate buffers\n";  
        ifile.close();  
        return;  
    }  
  
    while(!ifile.eof())  
    {  
        memset(obuff,0,(IBUFSIZE*2)+1);  
        memset(ibuff,0,IBUFSIZE);  
        ifile.read(ibuff,IBUFSIZE);  
  
        // corner case where file is exactly a multiple of  
        // 16 bytes in length  
        if(ibuff[0] == 0 && ifile.eof())  
            break;  
  
        for(i = 0; i < IBUFSIZE; i++)  
        {  
            if(ibuff[i] >= ' ')  
                obuff[i] = ibuff[i];  
            else  
                obuff[i] = '.';  
  
            cout << setfill('0') << setw(2) << hex  
                 << (int)ibuff[i] << ' ';  
        }  
        cout << "  " << obuff << endl;  
    }  
    ifile.close();  
}  
```  
  
  **十六進位傾印的 wcHello.txt \- 請注意輸出是 ANSI 字元：**  
**48 65 6c 6c 6f 20 57 6f 72 6c 64 00 00 00 00 00   Hello World.....  十六進位傾印的 wwHello.txt \- 請注意輸出是 wchar\_t 字元：**  
**48 00 65 00 6c 00 6c 00 6f 00 20 00 57 00 6f 00   H.e.l.l.o.  .W.o.  72 00 6c 00 64 00 00 00 00 00 00 00 00 00 00 00   r.l.d...........**    
### 建構函式  
  
|||  
|-|-|  
|[basic\_filebuf](../Topic/basic_filebuf::basic_filebuf.md)|建構類型 `basic_filebuf` 的物件。|  
  
### Typedefs  
  
|||  
|-|-|  
|[char\_type](../Topic/basic_filebuf::char_type.md)|將類型名稱與 `Elem` 樣板參數產生關聯。|  
|[int\_type](../Topic/basic_filebuf::int_type.md)|在 `basic_filebuf` 的範圍中製作此類型，相當於在 `Tr` 範圍中的同名類型。|  
|[off\_type](../Topic/basic_filebuf::off_type.md)|在 `basic_filebuf` 的範圍中製作此類型，相當於在 `Tr` 範圍中的同名類型。|  
|[pos\_type](../Topic/basic_filebuf::pos_type.md)|在 `basic_filebuf` 的範圍中製作此類型，相當於在 `Tr` 範圍中的同名類型。|  
|[traits\_type](../Topic/basic_filebuf::traits_type.md)|將類型名稱與 `Tr` 樣板參數產生關聯。|  
  
### 成員函式  
  
|||  
|-|-|  
|[關閉](../Topic/basic_filebuf::close.md)|關閉檔案。|  
|[is\_open](../Topic/basic_filebuf::is_open.md)|指出檔案是否為開啟。|  
|[開啟](../Topic/basic_filebuf::open.md)|開啟檔案。|  
|[Overflow \- 溢位](../Topic/basic_filebuf::overflow.md)|受保護的虛擬函式，可在將新字元插入已滿的緩衝區時呼叫。|  
|[pbackfail](../Topic/basic_filebuf::pbackfail.md)|受保護的虛擬成員函式會嘗試將項目放回輸入資料流，然後將其設成目前的項目 \(由下一個指標指向\)。|  
|[seekoff](../Topic/basic_filebuf::seekoff.md)|受保護的虛擬成員函式會嘗試改變受控制資料流的目前位置。|  
|[seekpos](../Topic/basic_filebuf::seekpos.md)|受保護的虛擬成員函式會嘗試改變受控制資料流的目前位置。|  
|[setbuf](../Topic/basic_filebuf::setbuf.md)|受保護的虛擬成員函式會執行每個衍生資料流緩衝區的特定作業。|  
|[Swap](../Topic/basic_filebuf::swap.md)|針對提供之 `basic_filebuf` 參數的內容，交換此 `basic_filebuf` 的內容。|  
|[sync](../Topic/basic_filebuf::sync.md)|受保護的虛擬函式會嘗試與任何相關聯的外部資料流同步處理控制資料流。|  
|[uflow](../Topic/basic_streambuf::uflow.md)|用於從輸入資料流擷取目前項目之受保護的虛擬函式。|  
|[溢位](../Topic/basic_filebuf::underflow.md)|用於從輸入資料流擷取目前項目之受保護的虛擬函式。|  
  
## 需求  
 **標頭：**\<fstream\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<fstream\>](../standard-library/fstream.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)