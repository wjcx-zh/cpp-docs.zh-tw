---
title: '&lt;fstream&gt; typedefs | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 49c5af53c6d174e7f87f75ad8970726c526db714
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962971"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt; typedefs

||||
|-|-|-|
|[filebuf](#filebuf)|[fstream](#fstream)|[ifstream](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[wifstream](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a>  filebuf

型別`basic_filebuf`特殊化**char**範本參數。

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>備註

類型是範本類別同義[basic_filebuf](../standard-library/basic-filebuf-class.md)類型的項目所特製化**char**具有預設字元特性。

## <a name="fstream"></a>  fstream

型別`basic_fstream`特殊化**char**範本參數。

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>備註

類型是範本類別同義[basic_fstream](../standard-library/basic-fstream-class.md)類型的項目所特製化**char**具有預設字元特性。

## <a name="ifstream"></a>  ifstream

定義用來從檔案連續讀取單一位元組字元的資料流。 `ifstream` 是特製化樣板類別的 typedef `basic_ifstream` for **char**。

另外還有`wifstream`，特製化的 typedef`basic_ifstream`讀取**wchar_t**全形字。 如需詳細資訊，請參閱 [wifstream](../standard-library/fstream-typedefs.md#wifstream)。

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>備註

類型是範本類別同義[basic_ifstream](../standard-library/basic-ifstream-class.md)、 具有預設字元特性的 char 類型的項目進行特製化。 例如，

`using namespace std;`

`ifstream infile("existingtextfile.txt");`

`if (!infile.bad())`

`{`

`// Dump the contents of the file to cout.`

`cout << infile.rdbuf();`

`infile.close();`

`}`

## <a name="ofstream"></a>  ofstream

型別`basic_ofstream`特殊化**char**範本參數。

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>備註

類型是範本類別同義[basic_ofstream](../standard-library/basic-ofstream-class.md)類型的項目所特製化**char**具有預設字元特性。

## <a name="wfstream"></a>  wfstream

型別`basic_fstream`特殊化**wchar_t**範本參數。

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>備註

類型是範本類別同義[basic_fstream](../standard-library/basic-fstream-class.md)類型的項目所特製化**wchar_t**具有預設字元特性。

## <a name="wifstream"></a>  wifstream

型別`basic_ifstream`特殊化**wchar_t**範本參數。

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>備註

類型是範本類別同義[basic_ifstream](../standard-library/basic-ifstream-class.md)類型的項目所特製化**wchar_t**具有預設字元特性。

## <a name="wofstream"></a>  wofstream

型別`basic_ofstream`特殊化**wchar_t**範本參數。

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>備註

類型是範本類別同義[basic_ofstream](../standard-library/basic-ofstream-class.md)類型的項目所特製化**wchar_t**具有預設字元特性。

## <a name="wfilebuf"></a>  wfilebuf

型別`basic_filebuf`特殊化**wchar_t**範本參數。

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>備註

類型是範本類別同義[basic_filebuf](../standard-library/basic-filebuf-class.md)類型的項目所特製化**wchar_t**具有預設字元特性。

## <a name="see-also"></a>另請參閱

[\<fstream>](../standard-library/fstream.md)<br/>
