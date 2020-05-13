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
ms.openlocfilehash: 0f63f65fb4c10fbe2ad538852222e6468b9061d0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375393"
---
# <a name="ltiosgt-typedefs"></a>&lt;ios&gt; typedef

## <a name="ios"></a><a name="ios"></a>Ios

支援來自舊 iostream 程式庫的 ios 類別。

```cpp
typedef basic_ios<char, char_traits<char>> ios;
```

### <a name="remarks"></a>備註

該類型是類範本[basic_ios](../standard-library/basic-ios-class.md)的同義詞,專門用於具有預設字元特徵的類型**字元**的元素。

## <a name="streamoff"></a><a name="streamoff"></a>流水

支援內部作業。

```cpp
#ifdef _WIN64
    typedef __int64 streamoff;
#else
    typedef long streamoff;
#endif
```

### <a name="remarks"></a>備註

此類型是帶正負號的整數，描述可儲存與各種資料流定位作業有關之位元組位移的物件。 其表示法至少有 32 值位元。 它不一定大到足以代表資料流內的任意位元組位置。 該值`streamoff(-1)`通常表示偏移錯誤。

## <a name="streampos"></a><a name="streampos"></a>流波

保留緩衝區指標或檔案指標的目前位置。

```cpp
typedef fpos<mbstate_t> streampos;
```

### <a name="remarks"></a>備註

該類型是[fpos](../standard-library/fpos-class.md) <  `mbstate_t`>的同义词。

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

## <a name="streamsize"></a><a name="streamsize"></a>流大小

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

## <a name="wios"></a><a name="wios"></a>威奧斯

支援來自舊 iostream 程式庫的 wios 類別。

```cpp
typedef basic_ios<wchar_t, char_traits<wchar_t>> wios;
```

### <a name="remarks"></a>備註

該類型是類範本[basic_ios](../standard-library/basic-ios-class.md)的同義詞,專門用於具有預設字元特徵的類型**wchar_t**元素。

## <a name="wstreampos"></a><a name="wstreampos"></a>wstreampos

保留緩衝區指標或檔案指標的目前位置。

```cpp
typedef fpos<mbstate_t> wstreampos;
```

### <a name="remarks"></a>備註

該類型是[fpos](../standard-library/fpos-class.md) <  `mbstate_t`>的同义词。

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
