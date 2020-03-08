---
title: '&lt;ios&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ios
- iosfwd/std::streamoff
- iosfwd/std::streampos
- iosfwd/std::streamsize
- iosfwd/std::wios
- iosfwd/std::wstreampos
ms.assetid: 0b962632-3439-44de-bf26-20c67a7f0ff3
ms.openlocfilehash: 20bffbeb7720274302633c5dda9e6364c06d5b54
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856389"
---
# <a name="ltiosgt-typedefs"></a>&lt;ios&gt; typedef

## <a name="ios"></a>ios

支援來自舊 iostream 程式庫的 ios 類別。

```cpp
typedef basic_ios<char, char_traits<char>> ios;
```

### <a name="remarks"></a>備註

此類型是類別樣板[basic_ios](../standard-library/basic-ios-class.md)的同義字，專門用於具有預設字元特性之**char**類型的元素。

## <a name="streamoff"></a>streamoff

支援內部作業。

```cpp
#ifdef _WIN64
    typedef __int64 streamoff;
#else
    typedef long streamoff;
#endif
```

### <a name="remarks"></a>備註

此類型是帶正負號整數，描述可儲存與各種資料流定位作業有關之位元組位移的物件。 其表示法至少有 32 值位元。 它不一定大到足以代表資料流內的任意位元組位置。 `streamoff(-1)` 的值通常表示有錯誤的位移。

## <a name="streampos"></a>streampos

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

此類型是類別樣板[basic_ios](../standard-library/basic-ios-class.md)的同義字，專門用於具有預設字元特性**wchar_t**類型的元素。

## <a name="wstreampos"></a>wstreampos

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
