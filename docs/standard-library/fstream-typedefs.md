---
title: '&lt;fstream&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- fstream/std::filebuf
- fstream/std::fstream
- fstream/std::ifstream
- fstream/std::ofstream
- fstream/std::wfilebuf
- fstream/std::wfstream
- fstream/std::wifstream
- fstream/std::wofstream
ms.assetid: 8dddef2d-7f17-42a6-ba08-6f6f20597d23
ms.openlocfilehash: 3b950192e098815739c30b732f1caee755c69f26
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835710"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt; typedefs

[filebuf](#filebuf)\
[a m](#fstream)\
[ifstream](#ifstream)\
[ofstream](#ofstream)\
[wfilebuf](#wfilebuf)\
[wfstream](#wfstream)\
[wifstream](#wifstream)\
[wofstream](#wofstream)

## <a name="filebuf"></a><a name="filebuf"></a> filebuf

`basic_filebuf`範本參數上特製化的型別 **`char`** 。

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>備註

此類型是類別樣板 [basic_filebuf](../standard-library/basic-filebuf-class.md)的同義字，專為 **`char`** 具有預設字元特性之類型的元素所特製化。

## <a name="fstream"></a><a name="fstream"></a> a m

`basic_fstream`範本參數上特製化的型別 **`char`** 。

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>備註

此類型是類別樣板 [basic_fstream](../standard-library/basic-fstream-class.md)的同義字，專為 **`char`** 具有預設字元特性之類型的元素所特製化。

## <a name="ifstream"></a><a name="ifstream"></a> ifstream

定義用來從檔案連續讀取單一位元組字元的資料流。 `ifstream` 是特製化類別範本的 typedef `basic_ifstream` **`char`** 。

另外還有 `wifstream` 一個會專門用 `basic_ifstream` 來讀取 **`wchar_t`** 雙範圍字元的 typedef。 如需詳細資訊，請參閱 [wifstream](../standard-library/fstream-typedefs.md#wifstream)。

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>備註

此類型是類別樣板 [basic_ifstream](../standard-library/basic-ifstream-class.md)的同義字，專為具有預設字元特性之 char 類型的元素所特製化。 例如，

```cpp
using namespace std;

ifstream infile("existingtextfile.txt");

if (!infile.bad())
{
    // Dump the contents of the file to cout.
    cout << infile.rdbuf();infile.close();
}
```

## <a name="ofstream"></a><a name="ofstream"></a> ofstream

`basic_ofstream`範本參數上特製化的型別 **`char`** 。

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>備註

此類型是類別樣板 [basic_ofstream](../standard-library/basic-ofstream-class.md)的同義字，專為 **`char`** 具有預設字元特性之類型的元素所特製化。

## <a name="wfstream"></a><a name="wfstream"></a> wfstream

`basic_fstream`範本參數上特製化的型別 **`wchar_t`** 。

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>備註

此類型是類別樣板 [basic_fstream](../standard-library/basic-fstream-class.md)的同義字，專為 **`wchar_t`** 具有預設字元特性之類型的元素所特製化。

## <a name="wifstream"></a><a name="wifstream"></a> wifstream

`basic_ifstream`範本參數上特製化的型別 **`wchar_t`** 。

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>備註

此類型是類別樣板 [basic_ifstream](../standard-library/basic-ifstream-class.md)的同義字，專為 **`wchar_t`** 具有預設字元特性之類型的元素所特製化。

## <a name="wofstream"></a><a name="wofstream"></a> wofstream

`basic_ofstream`範本參數上特製化的型別 **`wchar_t`** 。

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>備註

此類型是類別樣板 [basic_ofstream](../standard-library/basic-ofstream-class.md)的同義字，專為 **`wchar_t`** 具有預設字元特性之類型的元素所特製化。

## <a name="wfilebuf"></a><a name="wfilebuf"></a> wfilebuf

`basic_filebuf`範本參數上特製化的型別 **`wchar_t`** 。

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>備註

此類型是類別樣板 [basic_filebuf](../standard-library/basic-filebuf-class.md)的同義字，專為 **`wchar_t`** 具有預設字元特性之類型的元素所特製化。

## <a name="see-also"></a>另請參閱

[\<fstream>](../standard-library/fstream.md)
