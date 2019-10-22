---
title: '&lt;sstream&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::istringstream
- iosfwd/std::ostringstream
- iosfwd/std::stringbuf
- iosfwd/std::stringstream
- iosfwd/std::wistringstream
- iosfwd/std::wostringstream
- iosfwd/std::wstringbuf
- iosfwd/std::wstringstream
ms.assetid: d102edd2-ecea-4a35-a398-cf96e58dd422
ms.openlocfilehash: e8f5a20b976d196090ac9300510044e84470c462
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72686287"
---
# <a name="ltsstreamgt-typedefs"></a>&lt;sstream&gt; typedef

||||
|-|-|-|
|[istringstream](#istringstream)|[ostringstream](#ostringstream)|[stringbuf](#stringbuf)|
|[stringstream](#stringstream)|[wistringstream](#wistringstream)|[wostringstream](#wostringstream)|
|[wstringbuf](#wstringbuf)|[wstringstream](#wstringstream)|

## <a name="istringstream"></a>  istringstream

建立在**char**樣板參數上特製化 `basic_istringstream` 的類型。

```cpp
typedef basic_istringstream<char> istringstream;
```

### <a name="remarks"></a>備註

此類型是類別樣板[basic_istringstream](../standard-library/basic-istringstream-class.md)的同義字，專門用於類型為**char**的元素。

## <a name="ostringstream"></a>  ostringstream

建立在**char**樣板參數上特製化 `basic_ostringstream` 的類型。

```cpp
typedef basic_ostringstream<char> ostringstream;
```

### <a name="remarks"></a>備註

此類型是類別樣板[basic_ostringstream](../standard-library/basic-ostringstream-class.md)的同義字，專門用於類型為**char**的元素。

## <a name="stringbuf"></a>  stringbuf

建立在**char**樣板參數上特製化 `basic_stringbuf` 的類型。

```cpp
typedef basic_stringbuf<char> stringbuf;
```

### <a name="remarks"></a>備註

此類型是類別樣板[basic_stringbuf](../standard-library/basic-stringbuf-class.md)的同義字，專門用於類型為**char**的元素。

## <a name="stringstream"></a>  stringstream

建立在**char**樣板參數上特製化 `basic_stringstream` 的類型。

```cpp
typedef basic_stringstream<char> stringstream;
```

### <a name="remarks"></a>備註

此類型是類別樣板[basic_stringstream](../standard-library/basic-stringstream-class.md)的同義字，專門用於類型為**char**的元素。

## <a name="wistringstream"></a>  wistringstream

建立類型，`basic_istringstream` 在**wchar_t**樣板參數上特製化。

```cpp
typedef basic_istringstream<wchar_t> wistringstream;
```

### <a name="remarks"></a>備註

此類型是類別樣板[basic_istringstream](../standard-library/basic-istringstream-class.md)的同義字，專門用於類型**wchar_t**的元素。

## <a name="wostringstream"></a>  wostringstream

建立類型，`basic_ostringstream` 在**wchar_t**樣板參數上特製化。

```cpp
typedef basic_ostringstream<wchar_t> wostringstream;
```

### <a name="remarks"></a>備註

此類型是類別樣板[basic_ostringstream](../standard-library/basic-ostringstream-class.md)的同義字，專門用於類型**wchar_t**的元素。

## <a name="wstringbuf"></a>  wstringbuf

建立類型，`basic_stringbuf` 在**wchar_t**樣板參數上特製化。

```cpp
typedef basic_stringbuf<wchar_t> wstringbuf;
```

### <a name="remarks"></a>備註

此類型是類別樣板[basic_stringbuf](../standard-library/basic-stringbuf-class.md)的同義字，專門用於類型**wchar_t**的元素。

## <a name="wstringstream"></a>  wstringstream

建立類型，`basic_stringstream` 在**wchar_t**樣板參數上特製化。

```cpp
typedef basic_stringstream<wchar_t> wstringstream;
```

### <a name="remarks"></a>備註

此類型是類別樣板[basic_stringstream](../standard-library/basic-stringstream-class.md)的同義字，專門用於類型**wchar_t**的元素。

## <a name="see-also"></a>請參閱

[\<sstream>](../standard-library/sstream.md)
