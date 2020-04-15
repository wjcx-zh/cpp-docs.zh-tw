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
ms.openlocfilehash: 57e481c131a6e4a1111b1ed88217b891d6fc96a8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317186"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt; typedefs

||||
|-|-|-|
|[檔案](#filebuf)|[fstream](#fstream)|[如果流](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[威夫流](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a><a name="filebuf"></a>檔案

專門用於`basic_filebuf`**字元**模板參數的類型。

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>備註

該類型是類範本[basic_filebuf](../standard-library/basic-filebuf-class.md)的同義詞,專門用於具有預設字元特徵的類型**字元**的元素。

## <a name="fstream"></a><a name="fstream"></a>fstream

專門用於`basic_fstream`**字元**模板參數的類型。

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>備註

該類型是類範本[basic_fstream](../standard-library/basic-fstream-class.md)的同義詞,專門用於具有預設字元特徵的類型**字元**的元素。

## <a name="ifstream"></a><a name="ifstream"></a>如果流

定義用來從檔案連續讀取單一位元組字元的資料流。 `ifstream`是專門用於`basic_ifstream`**字元**的類範本的類型def。

還有`wifstream`,一個`basic_ifstream`專門 讀取**wchar_t**雙寬字元的類型。 如需詳細資訊，請參閱 [wifstream](../standard-library/fstream-typedefs.md#wifstream)。

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>備註

該類型是類範本[basic_ifstream](../standard-library/basic-ifstream-class.md)的同義詞,專門用於具有預設字元特徵的類型字元的元素。 例如，

```cpp
using namespace std;

ifstream infile("existingtextfile.txt");

if (!infile.bad())
{
    // Dump the contents of the file to cout.
    cout << infile.rdbuf();infile.close();
}
```

## <a name="ofstream"></a><a name="ofstream"></a>流

專門用於`basic_ofstream`**字元**模板參數的類型。

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>備註

該類型是類範本[basic_ofstream](../standard-library/basic-ofstream-class.md)的同義詞,專門用於具有預設字元特徵的類型**字元**的元素。

## <a name="wfstream"></a><a name="wfstream"></a>wfstream

專門用於`basic_fstream`**wchar_t**範本參數的類型。

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>備註

該類型是類範本[basic_fstream](../standard-library/basic-fstream-class.md)的同義詞,專門用於具有預設字元特徵的類型**wchar_t**元素。

## <a name="wifstream"></a><a name="wifstream"></a>威夫流

專門用於`basic_ifstream`**wchar_t**範本參數的類型。

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>備註

該類型是類範本[basic_ifstream](../standard-library/basic-ifstream-class.md)的同義詞,專門用於具有預設字元特徵**的類型wchar_t**元素。

## <a name="wofstream"></a><a name="wofstream"></a>沃夫流

專門用於`basic_ofstream`**wchar_t**範本參數的類型。

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>備註

該類型是類範本[basic_ofstream](../standard-library/basic-ofstream-class.md)的同義詞,專門用於具有預設字元特徵**的類型wchar_t**元素。

## <a name="wfilebuf"></a><a name="wfilebuf"></a>wfilebuf

專門用於`basic_filebuf`**wchar_t**範本參數的類型。

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>備註

該類型是類範本[basic_filebuf](../standard-library/basic-filebuf-class.md)的同義詞,專門用於具有預設字元特徵**的類型wchar_t**元素。

## <a name="see-also"></a>另請參閱

[\<>](../standard-library/fstream.md)
