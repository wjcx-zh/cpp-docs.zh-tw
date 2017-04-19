---
title: '&lt;ios&gt; typedef | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ios/std::ios
- ios/std::streamoff
- ios/std::streampos
- ios/std::streamsize
- ios/std::wios
- ios/std::wstreampos
ms.assetid: 0b962632-3439-44de-bf26-20c67a7f0ff3
caps.latest.revision: 13
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: d9f9dd5f13f0f4559455ff8d8cf09bab5350b1f0
ms.lasthandoff: 02/24/2017

---
# <a name="ltiosgt-typedefs"></a>&lt;ios&gt; typedef
||||  
|-|-|-|  
|[ios](#ios)|[streamoff](#streamoff)|[streampos](#streampos)|  
|[streamsize](#streamsize)|[wios](#wios)|[wstreampos](#wstreampos)|  
  
##  <a name="ios"></a>  ios  
 支援來自舊 iostream 程式庫的 ios 類別。  
  
```  
typedef basic_ios<char, char_traits<char>> ios;  
```  
  
### <a name="remarks"></a>備註  
 此類型與範本類別 [basic_ios](../standard-library/basic-ios-class.md) 同義，該範本類別是為具有預設字元特性之 `char` 類型的元素特製化的範本類別。  
  
##  <a name="streamoff"></a>  streamoff  
 支援內部作業。  
  
```  
#ifdef _WIN64  
    typedef __int64 streamoff;  
#else  
    typedef long streamoff;  
#endif  
```  
  
### <a name="remarks"></a>備註  
 此類型是帶正負號的整數，描述可儲存與各種資料流定位作業有關之位元組位移的物件。 其表示法至少有 32 值位元。 它不一定大到足以代表資料流內的任意位元組位置。 **streamoff(-1)** 值通常表示有錯誤的位移。  
  
##  <a name="streampos"></a>  streampos  
 保留緩衝區指標或檔案指標的目前位置。  
  
```  
typedef fpos<mbstate_t> streampos;  
```  
  
### <a name="remarks"></a>備註  
 此類型與 [fpos](../standard-library/fpos-class.md)< `mbstate_t`> 同義。  
  
### <a name="example"></a>範例  
  
```cpp  
// ios_streampos.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main( )   
{  
   using namespace std;  
  
   ofstream x( "iostream.txt" );  
   x << "testing";  
   streampos y = x.tellp( );  
   cout << y << endl;  
}  
```  
  
```Output  
7  
```  
  
##  <a name="streamsize"></a>  streamsize  
 表示資料流的大小。  
  
```  
#ifdef _WIN64  
    typedef __int64 streamsize;  
#else  
    typedef int streamsize;  
#endif  
```  
  
### <a name="remarks"></a>備註  
 此類型是帶正負號的整數，描述可儲存與各種資料流作業有關之元素數目計數的物件。 其表示法至少有 16 位元。 它不一定大到足以代表資料流內的任意位元組位置。  
  
### <a name="example"></a>範例  
  在編譯並執行下列程式之後，請檢閱 test.txt 檔案以查看設定 `streamsize` 的效果。  
  
```  
// ios_streamsize.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main( )   
{  
   using namespace std;  
   char a[16] = "any such text";  
   ofstream x( "test.txt" );  
   streamsize y = 6;  
   x.write( a, y );  
}  
```  
  
##  <a name="wios"></a>  wios  
 支援來自舊 iostream 程式庫的 wios 類別。  
  
```  
typedef basic_ios<wchar_t, char_traits<wchar_t>> wios;  
```  
  
### <a name="remarks"></a>備註  
 此類型與範本類別 [basic_ios](../standard-library/basic-ios-class.md) 同義，該範本類別是為具有預設字元特性之 `wchar_t` 類型的元素特製化的範本類別。  
  
##  <a name="wstreampos"></a>  wstreampos  
 保留緩衝區指標或檔案指標的目前位置。  
  
```  
typedef fpos<mbstate_t> wstreampos;  
```  
  
### <a name="remarks"></a>備註  
 此類型與 [fpos](../standard-library/fpos-class.md)< `mbstate_t`> 同義。  
  
### <a name="example"></a>範例  
  
```cpp  
// ios_wstreampos.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main( )   
{  
   using namespace std;  
   wofstream xw( "wiostream.txt" );  
   xw << L"testing";  
   wstreampos y = xw.tellp( );  
   cout << y << endl;  
}  
```  
  
```Output  
7  
```  
  
## <a name="see-also"></a>另請參閱  
 [\<ios>](../standard-library/ios.md)


