---
title: '&lt;iosfwd&gt;'
ms.date: 11/04/2016
f1_keywords:
- <iosfwd>
helpviewer_keywords:
- iosfwd header
ms.assetid: 964442eb-17f1-43ef-a0e0-c5bb77f9c187
ms.openlocfilehash: e9999d43226cb5daf22ef70af636efd616d41d47
ms.sourcegitcommit: 13f42c339fb7af935e3a93ac80e350d5e784c9f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2020
ms.locfileid: "87470949"
---
# <a name="ltiosfwdgt"></a>&lt;iosfwd&gt;

宣告 iostreams 中使用的數個類別樣板的向前參考。 所有這類類別範本都是在其他標準標頭中定義。 只有當您需要此標頭的其中一個宣告但不需要其定義時，才需要明確包含此標頭。

## <a name="syntax"></a>語法

```cpp
#include <iosfwd>
```

## <a name="typedefs"></a>Typedefs

```cpp
typedef T1 streamoff;
typedef T2 streamsize;
typedef fpos streampos;

// char TYPE DEFINITIONS
typedef basic_ios<char, char_traits<char>> ios;
typedef basic_streambuf<char, char_traits<char>> streambuf;
typedef basic_istream<char, char_traits<char>> istream;
typedef basic_ostream<char, char_traits<char>> ostream;
typedef basic_iostream<char, char_traits<char>> iostream;
typedef basic_stringbuf<char, char_traits<char>> stringbuf;
typedef basic_istringstream<char, char_traits<char>> istringstream;
typedef basic_ostringstream<char, char_traits<char>> ostringstream;
typedef basic_stringstream<char, char_traits<char>> stringstream;
typedef basic_filebuf<char, char_traits<char>> filebuf;
typedef basic_ifstream<char, char_traits<char>> ifstream;
typedef basic_ofstream<char, char_traits<char>> ofstream;
typedef basic_fstream<char, char_traits<char>> fstream;

// wchar_t TYPE DEFINITIONS
typedef basic_ios<wchar_t, char_traits<wchar_t>> wios;
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
typedef basic_stringbuf<wchar_t, char_traits<wchar_t>> wstringbuf;
typedef basic_istringstream<wchar_t, char_traits<wchar_t>> wistringstream;
typedef basic_ostringstream<wchar_t, char_traits<wchar_t>> wostringstream;
typedef basic_stringstream<wchar_t, char_traits<wchar_t>> wstringstream;
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

## <a name="forward-declarations-and-class-templates"></a>向前宣告和類別範本

```cpp
template <class _Statetype>
class fpos;

template <class Elem>;
class char_traits;

class char_traits<char>;

class char_traits<wchar_t>;

template <class T>
class allocator;

class ios_base;

template <class Elem, class Tr = char_traits<Elem>>
class basic_ios;

template <class Elem, class Tr = char_traits<Elem>>
class istreambuf_iterator;

template <class Elem, class Tr = char_traits<Elem>>
class ostreambuf_iterator;

template <class Elem, class Tr = char_traits<Elem>>
class basic_streambuf;

template <class Elem, class Tr = char_traits<Elem>>
class basic_istream;

template <class Elem, class Tr = char_traits<Elem>>
class basic_ostream;

template <class Elem, class Tr = char_traits<Elem>>
class basic_iostream;

template <class Elem, class Tr = char_traits<Elem>>
class basic_stringbuf;

template <class Elem, class Tr = char_traits<Elem>>
class basic_istringstream;

template <class Elem, class Tr = char_traits<Elem>>
class basic_ostringstream;

template <class Elem, class Tr = char_traits<Elem>>
class basic_stringstream;

template <class Elem, class Tr = char_traits<Elem>>
class basic_filebuf;

template <class Elem, class Tr = char_traits<Elem>>
class basic_ifstream;

template <class Elem, class Tr = char_traits<Elem>>
class basic_ofstream;

template <class Elem, class Tr = char_traits<Elem>>
class basic_fstream;
```

## <a name="see-also"></a>請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostreams 慣例](../standard-library/iostreams-conventions.md)
