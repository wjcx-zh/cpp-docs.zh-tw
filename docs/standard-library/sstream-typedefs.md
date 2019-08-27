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
ms.openlocfilehash: 27aed1d92b4893e054d7416dc5933ab23b843297
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451820"
---
# <a name="ltsstreamgt-typedefs"></a>&lt;sstream&gt; typedef

||||
|-|-|-|
|[istringstream](#istringstream)|[ostringstream](#ostringstream)|[stringbuf](#stringbuf)|
|[stringstream](#stringstream)|[wistringstream](#wistringstream)|[wostringstream](#wostringstream)|
|[wstringbuf](#wstringbuf)|[wstringstream](#wstringstream)|

## <a name="istringstream"></a>  istringstream

建立在`basic_istringstream` **char**樣板參數上特製化的型別。

```cpp
typedef basic_istringstream<char> istringstream;
```

### <a name="remarks"></a>備註

此類型與樣板類別[basic_istringstream](../standard-library/basic-istringstream-class.md)同義, 專門用於類型為**char**的元素。

## <a name="ostringstream"></a>  ostringstream

建立在`basic_ostringstream` **char**樣板參數上特製化的型別。

```cpp
typedef basic_ostringstream<char> ostringstream;
```

### <a name="remarks"></a>備註

此類型與樣板類別[basic_ostringstream](../standard-library/basic-ostringstream-class.md)同義, 專門用於類型為**char**的元素。

## <a name="stringbuf"></a>  stringbuf

建立在`basic_stringbuf` **char**樣板參數上特製化的型別。

```cpp
typedef basic_stringbuf<char> stringbuf;
```

### <a name="remarks"></a>備註

此類型與樣板類別[basic_stringbuf](../standard-library/basic-stringbuf-class.md)同義, 專門用於類型為**char**的元素。

## <a name="stringstream"></a>  stringstream

建立在`basic_stringstream` **char**樣板參數上特製化的型別。

```cpp
typedef basic_stringstream<char> stringstream;
```

### <a name="remarks"></a>備註

此類型與樣板類別[basic_stringstream](../standard-library/basic-stringstream-class.md)同義, 專門用於類型為**char**的元素。

## <a name="wistringstream"></a>  wistringstream

建立在`basic_istringstream` **wchar_t**樣板參數上特製化的類型。

```cpp
typedef basic_istringstream<wchar_t> wistringstream;
```

### <a name="remarks"></a>備註

此類型與樣板類別[basic_istringstream](../standard-library/basic-istringstream-class.md)同義, 專門用於**wchar_t**類型的元素。

## <a name="wostringstream"></a>  wostringstream

建立在`basic_ostringstream` **wchar_t**樣板參數上特製化的類型。

```cpp
typedef basic_ostringstream<wchar_t> wostringstream;
```

### <a name="remarks"></a>備註

此類型與樣板類別[basic_ostringstream](../standard-library/basic-ostringstream-class.md)同義, 專門用於**wchar_t**類型的元素。

## <a name="wstringbuf"></a>  wstringbuf

建立在`basic_stringbuf` **wchar_t**樣板參數上特製化的類型。

```cpp
typedef basic_stringbuf<wchar_t> wstringbuf;
```

### <a name="remarks"></a>備註

此類型與樣板類別[basic_stringbuf](../standard-library/basic-stringbuf-class.md)同義, 專門用於**wchar_t**類型的元素。

## <a name="wstringstream"></a>  wstringstream

建立在`basic_stringstream` **wchar_t**樣板參數上特製化的類型。

```cpp
typedef basic_stringstream<wchar_t> wstringstream;
```

### <a name="remarks"></a>備註

此類型與樣板類別[basic_stringstream](../standard-library/basic-stringstream-class.md)同義, 專門用於**wchar_t**類型的元素。

## <a name="see-also"></a>另請參閱

[\<sstream>](../standard-library/sstream.md)
