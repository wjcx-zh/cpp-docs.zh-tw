---
title: '&lt;ios&gt; typedef | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- iosfwd/std::ios
- iosfwd/std::streamoff
- iosfwd/std::streampos
- iosfwd/std::streamsize
- iosfwd/std::wios
- iosfwd/std::wstreampos
ms.assetid: 0b962632-3439-44de-bf26-20c67a7f0ff3
ms.openlocfilehash: d79e3361d58165ac356e2ef75c0a3fd1a4cb4f26
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963637"
---
# <a name="ltiosgt-typedefs"></a>&lt;ios&gt; typedef

||||
|-|-|-|
|[ios](#ios)|[streamoff](#streamoff)|[streampos](#streampos)|
|[streamsize](#streamsize)|[wios](#wios)|[wstreampos](#wstreampos)|

## <a name="ios"></a>  ios

支援來自舊 iostream 程式庫的 ios 類別。

```cpp
typedef basic_ios<char, char_traits<char>> ios;
```

### <a name="remarks"></a>備註

類型是範本類別同義[basic_ios](../standard-library/basic-ios-class.md)類型的項目所特製化**char**具有預設字元特性。

## <a name="streamoff"></a>  streamoff

支援內部作業。

```cpp
#ifdef _WIN64
    typedef __int64 streamoff;
#else
    typedef long streamoff;
#endif
```

### <a name="remarks"></a>備註

此類型是帶正負號的整數，描述可儲存與各種資料流定位作業有關之位元組位移的物件。 其表示法至少有 32 值位元。 它不一定大到足以代表資料流內的任意位元組位置。 值`streamoff(-1)`通常表示有錯誤的位移。

## <a name="streampos"></a>  streampos

保留緩衝區指標或檔案指標的目前位置。

```cpp
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

## <a name="streamsize"></a>  streamsize

表示資料流的大小。

```cpp
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

```cpp
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

## <a name="wios"></a>  wios

支援來自舊 iostream 程式庫的 wios 類別。

```cpp
typedef basic_ios<wchar_t, char_traits<wchar_t>> wios;
```

### <a name="remarks"></a>備註

類型是範本類別同義[basic_ios](../standard-library/basic-ios-class.md)類型的項目所特製化**wchar_t**具有預設字元特性。

## <a name="wstreampos"></a>  wstreampos

保留緩衝區指標或檔案指標的目前位置。

```cpp
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

[\<ios>](../standard-library/ios.md)<br/>
