---
title: '&lt;fstream&gt; typedefs | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 11
manager: ghogen
ms.openlocfilehash: 3fb38bcee6d23968e51e86fbde0b824cb7316ed4
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt; typedefs

||||
|-|-|-|
|[filebuf](#filebuf)|[fstream](#fstream)|[ifstream](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[wifstream](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a>  filebuf

`char` 範本參數上的特殊類型 `basic_filebuf`。

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>備註

這個類型與 [basic_filebuf](../standard-library/basic-filebuf-class.md) 範本類別同義，該範本類別是專為具有預設字元特性的 `char` 類型元素所特製化。

## <a name="fstream"></a>  fstream

`char` 範本參數上的特殊類型 `basic_fstream`。

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>備註

這個類型與範本類別 [basic_fstream](../standard-library/basic-fstream-class.md) 同義，該範本類別是專為具有預設字元特性的 `char` 類型元素所特製化。

## <a name="ifstream"></a>  ifstream

定義用來從檔案連續讀取單一位元組字元的資料流。 `ifstream` 是特製化 `basic_ifstream` 之樣板類別 `char` 的 typedef。

另外還有 `wifstream`，這是特製化 `basic_ifstream` 以讀取 `wchar_t` 全形字元的 typedef。 如需詳細資訊，請參閱 [wifstream](../standard-library/fstream-typedefs.md#wifstream)。

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>備註

類型是樣板類別的同義字[basic_ifstream](../standard-library/basic-ifstream-class.md)特製化的預設字元特性與 char 類型項目。 例如，

`using namespace std;`

`ifstream infile("existingtextfile.txt");`

`if (!infile.bad())`

`{`

`// Dump the contents of the file to cout.`

`cout << infile.rdbuf();`

`infile.close();`

`}`

## <a name="ofstream"></a>  ofstream

`char` 範本參數上的特殊類型 `basic_ofstream`。

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>備註

這個類型與 [basic_ofstream](../standard-library/basic-ofstream-class.md) 範本類別同義，該範本類別是專為具有預設字元特性的 `char` 類型元素所特製化。

## <a name="wfstream"></a>  wfstream

`wchar_t` 範本參數上的特殊類型 `basic_fstream`。

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>備註

這個類型與 [basic_fstream](../standard-library/basic-fstream-class.md) 範本類別同義，該範本類別是專為具有預設字元特性的 `wchar_t` 類型元素所特製化。

## <a name="wifstream"></a>  wifstream

`wchar_t` 範本參數上的特殊類型 `basic_ifstream`。

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>備註

這個類型與 [basic_ifstream](../standard-library/basic-ifstream-class.md) 範本類別同義，該範本類別是專為具有預設字元特性的 `wchar_t` 類型元素所特製化。

## <a name="wofstream"></a>  wofstream

`wchar_t` 範本參數上的特殊類型 `basic_ofstream`。

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>備註

這個類型與 [basic_ofstream](../standard-library/basic-ofstream-class.md) 範本類別同義，該範本類別是專為具有預設字元特性的 `wchar_t` 類型元素所特製化。

## <a name="wfilebuf"></a>  wfilebuf

`wchar_t` 範本參數上的特殊類型 `basic_filebuf`。

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>備註

這個類型與 [basic_filebuf](../standard-library/basic-filebuf-class.md) 範本類別同義，該範本類別是專為具有預設字元特性的 `wchar_t` 類型元素所特製化。

## <a name="see-also"></a>另請參閱

[\<fstream>](../standard-library/fstream.md)<br/>
