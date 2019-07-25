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
ms.openlocfilehash: 6144826254c6acc509db2c0285b21811fe37bd4e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454047"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt; typedefs

||||
|-|-|-|
|[filebuf](#filebuf)|[fstream](#fstream)|[ifstream](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[wifstream](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a>  filebuf

在`basic_filebuf` **char**樣板參數上特製化的類型。

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>備註

此類型與範本類別[basic_filebuf](../standard-library/basic-filebuf-class.md)同義, 專門用於具有預設字元特性之**char**類型的元素。

## <a name="fstream"></a>  fstream

在`basic_fstream` **char**樣板參數上特製化的類型。

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>備註

此類型與範本類別[basic_fstream](../standard-library/basic-fstream-class.md)同義, 專門用於具有預設字元特性之**char**類型的元素。

## <a name="ifstream"></a>  ifstream

定義用來從檔案連續讀取單一位元組字元的資料流。 `ifstream`是專門針對`basic_ifstream` **char**的樣板類別特製化的 typedef。

另外`wifstream`還有一個會專門`basic_ifstream`用來讀取**wchar_t**雙重寬字元的 typedef。 如需詳細資訊，請參閱 [wifstream](../standard-library/fstream-typedefs.md#wifstream)。

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>備註

此類型與範本類別[basic_ifstream](../standard-library/basic-ifstream-class.md)同義, 專門用於具有預設字元特性之 char 類型的元素。 例如，

```cpp
using namespace std;

ifstream infile("existingtextfile.txt");

if (!infile.bad())
{
    // Dump the contents of the file to cout.
    cout << infile.rdbuf();infile.close();
}
```

## <a name="ofstream"></a>  ofstream

在`basic_ofstream` **char**樣板參數上特製化的類型。

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>備註

此類型與範本類別[basic_ofstream](../standard-library/basic-ofstream-class.md)同義, 專門用於具有預設字元特性之**char**類型的元素。

## <a name="wfstream"></a>  wfstream

在`basic_fstream` **wchar_t**範本參數上特製化的類型。

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>備註

此類型與樣板類別[basic_fstream](../standard-library/basic-fstream-class.md)同義, 專門用於具有預設字元特性之**wchar_t**類型的元素。

## <a name="wifstream"></a>  wifstream

在`basic_ifstream` **wchar_t**範本參數上特製化的類型。

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>備註

此類型與樣板類別[basic_ifstream](../standard-library/basic-ifstream-class.md)同義, 專門用於具有預設字元特性之**wchar_t**類型的元素。

## <a name="wofstream"></a>  wofstream

在`basic_ofstream` **wchar_t**範本參數上特製化的類型。

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>備註

此類型與樣板類別[basic_ofstream](../standard-library/basic-ofstream-class.md)同義, 專門用於具有預設字元特性之**wchar_t**類型的元素。

## <a name="wfilebuf"></a>  wfilebuf

在`basic_filebuf` **wchar_t**範本參數上特製化的類型。

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>備註

此類型與樣板類別[basic_filebuf](../standard-library/basic-filebuf-class.md)同義, 專門用於具有預設字元特性之**wchar_t**類型的元素。

## <a name="see-also"></a>另請參閱

[\<fstream>](../standard-library/fstream.md)
