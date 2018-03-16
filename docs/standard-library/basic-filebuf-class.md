---
title: "basic_filebuf 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- fstream/std::basic_filebuf
- fstream/std::basic_filebuf::char_type
- fstream/std::basic_filebuf::int_type
- fstream/std::basic_filebuf::off_type
- fstream/std::basic_filebuf::pos_type
- fstream/std::basic_filebuf::traits_type
- fstream/std::basic_filebuf::close
- fstream/std::basic_filebuf::is_open
- fstream/std::basic_filebuf::open
- fstream/std::basic_filebuf::overflow
- fstream/std::basic_filebuf::pbackfail
- fstream/std::basic_filebuf::seekoff
- fstream/std::basic_filebuf::seekpos
- fstream/std::basic_filebuf::setbuf
- fstream/std::basic_filebuf::Swap
- fstream/std::basic_filebuf::sync
- fstream/std::basic_filebuf::uflow
- fstream/std::basic_filebuf::underflow
dev_langs:
- C++
helpviewer_keywords:
- std::basic_filebuf [C++]
- std::basic_filebuf [C++], char_type
- std::basic_filebuf [C++], int_type
- std::basic_filebuf [C++], off_type
- std::basic_filebuf [C++], pos_type
- std::basic_filebuf [C++], traits_type
- std::basic_filebuf [C++], close
- std::basic_filebuf [C++], is_open
- std::basic_filebuf [C++], open
- std::basic_filebuf [C++], overflow
- std::basic_filebuf [C++], pbackfail
- std::basic_filebuf [C++], seekoff
- std::basic_filebuf [C++], seekpos
- std::basic_filebuf [C++], setbuf
- std::basic_filebuf [C++], Swap
- std::basic_filebuf [C++], sync
- std::basic_filebuf [C++], uflow
- std::basic_filebuf [C++], underflow
ms.assetid: 3196ba5c-bf38-41bd-9a95-70323ddfca1a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5c9891f67c376d13794778c82b167092237df3f7
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2018
---
# <a name="basicfilebuf-class"></a>basic_filebuf 類別
描述資料流緩衝區，其控制類型 `Elem` 的項目 (其字元特性由類別 `Tr` 所決定)，與外部檔案中儲存的項目序列之間的往來傳輸。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Elem, class Tr = char_traits<Elem>>  
class basic_filebuf : public basic_streambuf<Elem, Tr>  
```  
  
#### <a name="parameters"></a>參數  
 `Elem`  
 檔案緩衝區的基本項目。  
  
 `Tr`  
 檔案緩衝區之基本元素的特性 (通常是 `char_traits`< `Elem`>)。  
  
## <a name="remarks"></a>備註  
 範本類別描述資料流緩衝區，其控制類型 `Elem` 的項目 (其字元特性由類別 `Tr` 所決定)，與外部檔案中儲存的項目序列之間的往來傳輸。  
  
> [!NOTE]
>  類型 `basic_filebuf` 的物件是在類型 `char *` 的內部緩衝區內建立，不論類型參數 `Elem` 所指定的 `char_type`。 這表示在寫入內部緩衝區之前，Unicode 字串 (包含 `wchar_t` 字元) 會轉換為 ANSI 字串 (包含 `char` 字元)。 若要在緩衝區中儲存 Unicode 字串，請建立 `wchar_t` 類型的新緩衝區，並使用 [basic_streambuf::pubsetbuf](../standard-library/basic-streambuf-class.md#pubsetbuf)`()` 方法來設定它。 若要查看示範此行為的範例，請參閱以下範例。  
  
 類別 `basic_filebuf`< `Elem`, `Tr`> 的物件會儲存檔案指標，而檔案指標指定 `FILE` 物件以控制與開啟的檔案相關聯的資料流。 它也會將指標儲存至兩個檔案轉換 Facet，以供受保護成員函式 [overflow](#overflow) 和 [underflow](#underflow) 使用。 如需詳細資訊，請參閱 [basic_filebuf::open](#open)。  
  
## <a name="example"></a>範例  
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
  
```Output  
Hex Dump of wcHello.txt - note that output is ANSI chars:  
48 65 6c 6c 6f 20 57 6f 72 6c 64 00 00 00 00 00   Hello World.....  
  
Hex Dump of wwHello.txt - note that output is wchar_t chars:  
48 00 65 00 6c 00 6c 00 6f 00 20 00 57 00 6f 00   H.e.l.l.o. .W.o.  
72 00 6c 00 64 00 00 00 00 00 00 00 00 00 00 00   r.l.d...........  
```  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[basic_filebuf](#basic_filebuf)|建構類型 `basic_filebuf` 的物件。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#char_type)|將類型名稱與 `Elem` 樣板參數產生關聯。|  
|[int_type](#int_type)|在 `basic_filebuf` 的範圍中製作此類型，相當於在 `Tr` 範圍中的同名類型。|  
|[off_type](#off_type)|在 `basic_filebuf` 的範圍中製作此類型，相當於在 `Tr` 範圍中的同名類型。|  
|[pos_type](#pos_type)|在 `basic_filebuf` 的範圍中製作此類型，相當於在 `Tr` 範圍中的同名類型。|  
|[traits_type](#traits_type)|將類型名稱與 `Tr` 樣板參數產生關聯。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[close](#close)|關閉檔案。|  
|[is_open](#is_open)|指出檔案是否為開啟。|  
|[open](#open)|開啟檔案。|  
|[overflow](#overflow)|受保護的虛擬函式，可在將新字元插入已滿的緩衝區時呼叫。|  
|[pbackfail](#pbackfail)|受保護的虛擬成員函式會嘗試將項目放回輸入資料流，然後將其設成目前的項目 (由下一個指標指向)。|  
|[seekoff](#seekoff)|受保護的虛擬成員函式會嘗試改變受控制資料流的目前位置。|  
|[seekpos](#seekpos)|受保護的虛擬成員函式會嘗試改變受控制資料流的目前位置。|  
|[setbuf](#setbuf)|受保護的虛擬成員函式會執行每個衍生資料流緩衝區的特定作業。|  
|[Swap](#swap)|針對提供之 `basic_filebuf` 參數的內容，交換此 `basic_filebuf` 的內容。|  
|[sync](#sync)|受保護的虛擬函式會嘗試與任何相關聯的外部資料流同步處理控制資料流。|  
|[uflow](../standard-library/basic-streambuf-class.md#uflow)|用於從輸入資料流擷取目前項目之受保護的虛擬函式。|  
|[underflow](#underflow)|用於從輸入資料流擷取目前項目之受保護的虛擬函式。|  
  
## <a name="requirements"></a>需求  
 **標頭：**\<fstream>  
  
 **命名空間：** std  
  
##  <a name="basic_filebuf"></a> basic_filebuf::basic_filebuf  
 建構類型 `basic_filebuf` 的物件。  
  
```  
basic_filebuf();

basic_filebuf(basic_filebuf&& right);
```  
  
### <a name="remarks"></a>備註  
 第一個建構函式會在控制輸入緩衝區和輸出緩衝區的所有指標中儲存 Null 指標。 它也會將 Null 指標儲存在檔案指標中。  
  
 第二個建構函式會使用視為右值參考的 `right` 內容初始化物件。  
  
##  <a name="char_type"></a> basic_filebuf::char_type  
 將類型名稱與 **Elem** 範本參數建立關聯。  
  
```  
typedef Elem char_type;  
```  
  
##  <a name="close"></a> basic_filebuf::close  
 關閉檔案。  
  
```  
basic_filebuf<Elem, Tr> *close();
```  
  
### <a name="return-value"></a>傳回值  
 如果檔案指標為 Null 指標，則成員函式會傳回 Null 指標。  
  
### <a name="remarks"></a>備註  
 **close** 會呼叫 `fclose`(**fp**)。 如果該函式傳回非零值，則函式會傳回 Null 指標。 否則，它會傳回 **this**，表示已成功關閉檔案。  
  
 針對寬資料流，如果在開啟資料流之後或最後一次呼叫 `streampos` 之後進行過任何插入，則函式會呼叫 [overflow](#overflow)。 它也會插入還原初始轉換狀態所需的任何序列，方法是視需要使用檔案轉換 Facet **fac** 來呼叫 **fac.unshift**。 因此，產生之 `char` 類型的每個元素 **byte** 都會寫入至檔案指標 **fp** 所指定的相關聯資料流，就像後續呼叫 `fputc`(**byte**, **fp**) 形式一樣。 如果 **fac.unshift** 呼叫或任何寫入失敗，則函式會失敗。  
  
### <a name="example"></a>範例  
  下列範例假設目前目錄中有兩個檔案︰basic_filebuf_close.txt (內容為 "testing") 和 iotest.txt (內容為 "ssss")。  
  
```  
// basic_filebuf_close.cpp  
// compile with: /EHsc  
#include <fstream>  
#include <iostream>  
  
int main() {  
   using namespace std;  
   ifstream file;  
   basic_ifstream <wchar_t> wfile;  
   char c;  
   // Open and close with a basic_filebuf  
   file.rdbuf()->open( "basic_filebuf_close.txt", ios::in );  
   file >> c;  
   cout << c << endl;  
   file.rdbuf( )->close( );  
  
   // Open/close directly  
   file.open( "iotest.txt" );  
   file >> c;  
   cout << c << endl;  
   file.close( );  
  
   // open a file with a wide character name  
   wfile.open( L"iotest.txt" );  
  
   // Open and close a nonexistent with a basic_filebuf  
   file.rdbuf()->open( "ziotest.txt", ios::in );  
   cout << file.fail() << endl;  
   file.rdbuf( )->close( );  
  
   // Open/close directly  
   file.open( "ziotest.txt" );  
   cout << file.fail() << endl;  
   file.close( );  
}  
```  
  
```Output  
t  
s  
0  
1  
```  
  
##  <a name="int_type"></a> basic_filebuf::int_type  
 使 basic_filebuf 範圍中的這個類型，相當於 **Tr** 範圍中的同名類型。  
  
```  
typedef typename traits_type::int_type int_type;  
```  
  
##  <a name="is_open"></a> basic_filebuf::is_open  
 指出檔案是否為開啟。  
  
```  
bool is_open() const;
```  
  
### <a name="return-value"></a>傳回值  
 如果檔案指標不為 Null 指標，則為 **true**。  
  
### <a name="example"></a>範例  
  
```cpp  
// basic_filebuf_is_open.cpp  
// compile with: /EHsc  
#include <fstream>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   ifstream file;  
   cout << boolalpha << file.rdbuf( )->is_open( ) << endl;  
  
   file.open( "basic_filebuf_is_open.cpp" );  
   cout << file.rdbuf( )->is_open( ) << endl;  
}  
```  
  
```Output  
false  
true  
```  
  
##  <a name="off_type"></a> basic_filebuf::off_type  
 使 basic_filebuf 範圍中的這個類型，相當於 **Tr** 範圍中的同名類型。  
  
```  
typedef typename traits_type::off_type off_type;  
```  
  
##  <a name="open"></a> basic_filebuf::open  
 開啟檔案。  
  
```  
basic_filebuf<Elem, Tr> *open(
    const char* _Filename,  
    ios_base::openmode _Mode,  
    int _Prot = (int)ios_base::_Openprot);

basic_filebuf<Elem, Tr> *open(
    const char* _Filename,  
    ios_base::openmode _Mode);

basic_filebuf<Elem, Tr> *open(
    const wchar_t* _Filename,  
    ios_base::openmode _Mode,  
    int _Prot = (int)ios_base::_Openprot);

basic_filebuf<Elem, Tr> *open(
    const wchar_t* _Filename,  
    ios_base::openmode _Mode);
```  
  
### <a name="parameters"></a>參數  
 `_Filename`  
 要開啟之檔案的名稱。  
  
 `_Mode`  
 [ios_base::openmode](../standard-library/ios-base-class.md#openmode) 中的其中一個列舉。  
  
 `_Prot`  
 預設檔案開啟保護，相當於 [_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md) 中的 `shflag` 參數。  
  
### <a name="return-value"></a>傳回值  
 如果檔案指標為 Null 指標，則函式會傳回 Null 指標。 否則，它會傳回 **this**。  
  
### <a name="remarks"></a>備註  
 成員函式會開啟檔名為 *filename* 的檔案，方法是呼叫 [fopen](../c-runtime-library/reference/fopen-wfopen.md)( *filename*, **strmode**)。 **strmode** 取決於 **mode &**~( [ate](../standard-library/ios-base-class.md#openmode) & &#124; [binary](../standard-library/ios-base-class.md#openmode))：  
  
- **ios_base::in** 變成 **"r"** (開啟現有檔案進行讀取)。  
  
- [ios_base::out](../standard-library/ios-base-class.md#fmtflags) 或 **ios_base::out &#124; ios_base::trunc** 變成 **"w"** (截斷現有檔案，或建立以進行寫入)。  
  
- **ios_base::out &#124; app** 變成 **"a"** (開啟現有檔案以附加所有寫入)。  
  
- **ios_base::in &#124; ios_base::out** 變成 **"r+"** (開啟現有檔案以進行讀取和寫入)。  
  
- **ios_base::in &#124; ios_base::out &#124; ios_base::trunc** 變成 **"w+"** (截斷現有檔案，或建立以進行讀取和寫入)。  
  
- **ios_base::in &#124; ios_base::out &#124; ios_base::app** 變成 **"a+"** (開啟現有檔案以讀取和附加所有寫入)。  
  
 如果 **mode & ios_base::binary** 為非零，則此函式會將 **b** 附加至 **strmode**以開啟二進位資料流，而不是文字資料流。 它接著會將 `fopen` 所傳回的值儲存在檔案指標 **fp** 中。 如果 **mode & ios_base::ate** 為非零，而且檔案指標不是 Null 指標，則此函式會呼叫 `fseek`( **fp**, 0, `SEEK_END`) 以在檔案結尾放置資料流。 如果該定位作業失敗，則函式會呼叫 [close](#close)(**fp**)，並將 Null 指標儲存在檔案指標中。  
  
 如果檔案指標不是 Null 指標，則此函式會判斷檔案轉換 Facet：`use_facet`< `codecvt`< **Elem**, `char`, **traits_type::**[state_type](../standard-library/char-traits-struct.md#state_type)> >( [getloc](../standard-library/basic-streambuf-class.md#getloc))，以供 [underflow](#underflow) 和 [overflow](#overflow) 使用。  
  
 如果檔案指標為 Null 指標，則函式會傳回 Null 指標。 否則，它會傳回 **this**。  
  
### <a name="example"></a>範例  
  如需使用 **open** 的範例，請參閱 [basic_filebuf::close](#close)。  
  
##  <a name="op_eq"></a> basic_filebuf::operator=  
 指派此資料流緩衝區物件的內容。 這是一個移動指派，涉及不會留下複本的右值。  
  
```  
basic_filebuf& operator=(basic_filebuf&& right);
```  
  
### <a name="parameters"></a>參數  
 `right`  
 [basic_filebuf](../standard-library/basic-filebuf-class.md) 物件的右值參考。  
  
### <a name="return-value"></a>傳回值  
 傳回 *this。  
  
### <a name="remarks"></a>備註  
 成員運算子會使用 `right` 的內容 (被視為 rvalue 參考) 來取代物件的內容。 如需詳細資訊，請參閱[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
##  <a name="overflow"></a> basic_filebuf::overflow  
 將新字元插入已滿的緩衝區時呼叫。  
  
```  
virtual int_type overflow(int_type _Meta = traits_type::eof);
```  
  
### <a name="parameters"></a>參數  
 `_Meta`  
 要插入緩衝區的字元，或 **traits_type::eof**。  
  
### <a name="return-value"></a>傳回值  
 如果函式不成功，則傳回 **traits_type::eof**。 否則會傳回 **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*)。  
  
### <a name="remarks"></a>備註  
 如果 _ * 中繼 ***！ = traits_type::**[eof](../standard-library/char-traits-struct.md#eof)，受保護的虛擬成員函式儘量插入項目的**ch = traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(\_ *中繼*) 至輸出緩衝區。 它可以透過下列各種方式來執行：  
  
-   如果有寫入位置可供使用，它可以將元素儲存在寫入位置，並遞增輸出緩衝區的下一個指標。  
  
-   為輸出緩衝區配置新的或額外的儲存空間，即可提供寫入位置。  
  
-   它可以轉換輸出緩衝區中的任何暫止輸出，後接 **ch**，方法是視需要使用檔案轉換 Facet **fac** 來呼叫 **fac.out**。 因此，產生之 *char* 類型的每個元素 `ch` 都會寫入至檔案指標 **fp** 所指定的相關聯資料流，就像後續呼叫 `fputc`(**ch**, **fp**) 形式一樣。 如果任何轉換或寫入失敗，則函式會失敗。  
  
##  <a name="pbackfail"></a> basic_filebuf::pbackfail  
 嘗試將元素放回輸入資料流，然後將其設成目前元素 (透過下一個指標所指向)。  
  
```  
virtual int_type pbackfail(int_type _Meta = traits_type::eof);
```  
  
### <a name="parameters"></a>參數  
 `_Meta`  
 要插入緩衝區的字元，或 **traits_type::eof**。  
  
### <a name="return-value"></a>傳回值  
 如果函式不成功，則傳回 **traits_type::eof**。 否則會傳回 **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*)。  
  
### <a name="remarks"></a>備註  
 受保護虛擬成員函式會將元素放回輸入緩衝區，然後將其設成目前元素 (透過下一個指標所指向)。 如果 _*Meta* **== traits_type::**[eof](../standard-library/char-traits-struct.md#eof)，要推回的元素實際上是一個已在資料流中目前元素之前的元素。 否則會以 **ch = traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(\_ *Meta*) 取代該元素。 函式可透過下列各種方式來放回項目：  
  
-   如果有 putback 位置可供使用，而且儲存在其中的元素與 **ch** 相等，則可遞減輸入緩衝區的下一個指標。  
  
-   如果函式可讓 `putback` 位置可供使用，則可以這麼做，並將下一個指標設定為指向該位置，然後將 **ch** 儲存在該位置中。  
  
-   如果函式可以推送回元素的輸入資料流，它可以這樣做，例如藉由呼叫`ungetc`項目的型別`char`。  
  
##  <a name="pos_type"></a> basic_filebuf::pos_type  
 使 basic_filebuf 範圍中的這個類型，相當於 **Tr** 範圍中的同名類型。  
  
```  
typedef typename traits_type::pos_type pos_type;  
```  
  
##  <a name="seekoff"></a> basic_filebuf::seekoff  
 嘗試改變受控制資料流的目前位置。  
  
```  
virtual pos_type seekoff(off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```  
  
### <a name="parameters"></a>參數  
 `_Off`  
 要搜尋的 `_Way` 相對位置。  
  
 `_Way`  
 位移作業的起點。 如需可能的值，請參閱 [seekdir](../standard-library/ios-base-class.md#seekdir)。  
  
 `_Which`  
 指定指標位置的模式。 預設為允許您修改讀取和寫入位置。  
  
### <a name="return-value"></a>傳回值  
 傳回新位置或無效的資料流位置。  
  
### <a name="remarks"></a>備註  
 受保護的虛擬成員函式會致力於改變受控制資料流的目前位置。 對於類別 [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`> 的物件，`fpos_t` 類型的物件可以代表資料流位置，這類型的物件可儲存用來剖析寬資料流所需的位移和任何狀態資訊。 位移零指定資料流的第一個元素 ([pos_type](../standard-library/basic-streambuf-class.md#pos_type) 類型的物件會儲存至少一個 `fpos_t` 物件)。  
  
 針對開啟進行讀取和寫入的檔案，輸入和輸出資料流會一前一後地放置在一起。 若要切換插入與擷取，您必須呼叫 [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff) 或 [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos)。 `pubseekoff` 呼叫 (因而 `seekoff` 呼叫) 具有[文字資料流](../c-runtime-library/text-and-binary-streams.md)、[二進位資料流](../c-runtime-library/text-and-binary-streams.md)和[寬資料流](../c-runtime-library/byte-and-wide-streams.md)的各種限制。  
  
 如果檔案指標 **fp** 為 Null 指標，則函式失敗。 否則，它會致力於呼叫 `fseek`( **fp**, `_Off`, `_Way`) 來改變資料流位置。 如果該函式成功，而且可以呼叫 `fgetpos`( **fp**, **&fposn**) 來決定所產生的位置 **fposn**，則函式會成功。 如果函式成功，則會傳回包含 **fposn**的 **pos_type** 類型值。 否則會傳回無效的資料流位置。  
  
##  <a name="seekpos"></a> basic_filebuf::seekpos  
 嘗試改變受控制資料流的目前位置。  
  
```  
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```  
  
### <a name="parameters"></a>參數  
 `_Sp`  
 要搜尋的位置。  
  
 `_Which`  
 指定指標位置的模式。 預設為允許您修改讀取和寫入位置。  
  
### <a name="return-value"></a>傳回值  
 如果檔案指標 **fp** 為 Null 指標，則函式失敗。 否則，它會致力於呼叫 `fsetpos`( **fp**, **&fposn**) 來改變資料流位置，其中 **fposn** 是 `pos` 中所儲存的 `fpos_t` 物件。 如果該函式成功，則函式會傳回 `pos`。 否則會傳回無效的資料流位置。 若要判斷資料流位置是否無效，請比較傳回值與 `pos_type(off_type(-1))`。  
  
### <a name="remarks"></a>備註  
 受保護虛擬成員函式會致力於改變受控制資料流的目前位置。 對於類別 [basic_filebuf](../standard-library/basic-filebuf-class.md)\< **Elem**, **Tr**> 的物件，`fpos_t` 類型的物件可以代表資料流位置，這類型的物件可儲存用來剖析寬資料流所需的位移和任何狀態資訊。 位移零指定資料流的第一個元素 (`pos_type` 類型的物件會儲存至少一個 `fpos_t` 物件)。  
  
 針對開啟進行讀取和寫入的檔案，輸入和輸出資料流會一前一後地放置在一起。 若要切換插入與擷取，您必須呼叫 [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff) 或 [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos)。 `pubseekoff` 呼叫 (因而 `seekoff` 呼叫) 具有文字資料流、二進位資料流和寬資料流的各種限制。  
  
 針對寬資料流，如果在開啟資料流之後或最後一次呼叫 `streampos` 之後進行過任何插入，則函式會呼叫 [overflow](#overflow)。 它也會插入還原初始轉換狀態所需的任何序列，方法是視需要使用檔案轉換 Facet **fac** 來呼叫 **fac**`.unshift`。 因此，產生之 `char` 類型的每個元素 **byte** 都會寫入至檔案指標 **fp** 所指定的相關聯資料流，就像後續呼叫 `fputc`(**byte**, **fp**) 形式一樣。 如果 **fac.unshift** 呼叫或任何寫入失敗，則函式會失敗。  
  
##  <a name="setbuf"></a> basic_filebuf::setbuf  
 執行每個衍生資料流緩衝區的特定作業。  
  
```  
virtual basic_streambuf<Elem, Tr> *setbuf(
    char_type* _Buffer,  
    streamsize count);
```  
  
### <a name="parameters"></a>參數  
 `_Buffer`  
 緩衝區的指標。  
  
 `count`  
 緩衝區的大小。  
  
### <a name="return-value"></a>傳回值  
 如果檔案指標 `fp` 為 Null 指標，則受保護成員函式會傳回零。  
  
### <a name="remarks"></a>備註  
 `setbuf` 會呼叫 `setvbuf`( **fp**, ( `char` \*) `_Buffer`, `_IOFBF`, `count` \* `sizeof` ( **Elem**) ) 以提供開始於 _*Buffer* 之 `count` 元素的陣列，作為資料流的緩衝區。 如果該函式傳回非零值，則函式會傳回 Null 指標。 否則，它會傳回 **this** 以發出成功訊號。  
  
##  <a name="swap"></a> basic_filebuf::swap  
 將這個 `basic_filebuf` 的內容和提供的 `basic_filebuf` 內容交換。  
  
```  
void swap(basic_filebuf& right);
```  
  
### <a name="parameters"></a>參數  
 `right`  
 對其他 `basic_filebuf` 的 `lvalue` 參考。  
  
##  <a name="sync"></a> basic_filebuf::sync  
 嘗試與任何相關聯外部資料流同步處理受控制資料流。  
  
```  
virtual int sync();
```  
  
### <a name="return-value"></a>傳回值  
 如果檔案指標 **fp** 為 Null 指標，則會傳回零。 否則，只有在 [overflow](#overflow) 和 `fflush`( **fp**) 呼叫成功將任何暫止輸出清除到資料流時，才會傳回零。  
  
##  <a name="traits_type"></a> basic_filebuf::traits_type  
 將類型名稱與 **Tr** 範本參數建立關聯。  
  
```  
typedef Tr traits_type;  
```  
  
##  <a name="underflow"></a> basic_filebuf::underflow  
 從輸入資料流擷取目前元素。  
  
```  
virtual int_type underflow();
```  
  
### <a name="return-value"></a>傳回值  
 如果函式不成功，則傳回 **traits_type::**[eof](../standard-library/char-traits-struct.md#eof)。 否則，它會傳回如＜備註＞小節所述進行轉換的 **ch**。  
  
### <a name="remarks"></a>備註  
 受保護虛擬成員函式會致力於從輸入緩衝區中擷取目前元素 **ch**，並將此元素傳回為 **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **ch**)。 它可以透過下列各種方式來執行：  
  
-   如果有讀取位置可供使用，它會接受 **ch** 作為儲存在讀取位置中的元素，並前進到輸入緩衝區的下一個指標。  
  
-   它可以讀取類型的一或多個項目`char`，像是由表單的後續呼叫`fgetc`(**fp**)，並將其轉換的項目**ch**型別的**Elem**呼叫使用檔案轉換 facet /fac **fac.in**視。 如果任何讀取或轉換失敗，則函式會失敗。  
  
## <a name="see-also"></a>另請參閱  
 [\<fstream>](../standard-library/fstream.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostream 慣例](../standard-library/iostreams-conventions.md)

