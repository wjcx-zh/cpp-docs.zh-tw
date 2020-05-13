---
title: '&lt;iostream&gt;'
ms.date: 09/20/2017
f1_keywords:
- <iostream>
- iostream/std::cerr
- iostream/std::cin
- iostream/std::clog
- iostream/std::cout
- iostream/std::wcerr
- iostream/std::wcin
- iostream/std::wclog
- iostream/std::wcout
helpviewer_keywords:
- iostream header
ms.assetid: de5d39e1-7e77-4b55-bcd1-7c77b41515c8
ms.openlocfilehash: 03afb777dc3926284cf0dc625e94a716ecdf5413
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375350"
---
# <a name="ltiostreamgt"></a>&lt;iostream&gt;

宣告對標準資料流的讀取和寫入進行控制的物件。 這通常包括您需要從C++程式進行輸入和輸出的唯一標頭。

## <a name="syntax"></a>語法

```cpp
#include <iostream>
```

> [!NOTE]
> \<iostream`#include <ios>`>库使用`#include <streambuf>``#include <istream>``#include <ostream>`、 和 語句。

## <a name="remarks"></a>備註

這些物件可分為兩個群組：

- [ ](#cin)cin、cout、cerr 和[clog](#clog)都是面向位元組的,執行傳統的位元[cout](#cout)[cerr](#cerr)組一次傳輸。

- [wcin](#wcin)、[wcout](#wcout)、[wcerr](#wcerr) 及 [wclog](#wclog) 是寬字元導向物件，會對程式在內部操作的寬字元進行雙向轉譯。

對流執行某些操作(如標準輸入)后,不能在同一流上執行不同方向的操作。 因此,例如,程式不能在[cin](#cin)和[wcin](#wcin)上互換運行。

在此標頭中聲明的所有物件都共用一個奇特的屬性 - 您可以假定它們是在您定義的任何靜態物件之前構造的,\<在包含 iostream>的转换单元中。 同樣,您可以假定這些物件不會在您定義的任何此類靜態對象的析構函數之前銷毀。 (但是,輸出流在程序終止期間被刷新。因此,您可以在程式啟動之前和程序終止後安全地讀取或寫入標準流。

然而,這種保證並不普遍。 靜態建構函式可能會在另一個轉譯單位中呼叫函式。 由於轉換單元參與靜態構造的順序不確定,被調用函數不能假定在此標頭中聲明的物件已構造。 若要在這類內容中使用這些物件，您必須先建構 [ios_base::Init](../standard-library/ios-base-class.md#init) 類別的物件。

### <a name="global-stream-objects"></a>全域資料流物件

|||
|-|-|
|[cerr](#cerr)|指定 `cerr` 全域資料流。|
|[Cin](#cin)|指定 `cin` 全域資料流。|
|[堵塞](#clog)|指定 `clog` 全域資料流。|
|[cout](#cout)|指定 `cout` 全域資料流。|
|[wcerr](#wcerr)|指定 `wcerr` 全域資料流。|
|[wc因](#wcin)|指定 `wcin` 全域資料流。|
|[wclog](#wclog)|指定 `wclog` 全域資料流。|
|[wcout](#wcout)|指定 `wcout` 全域資料流。|

### <a name="cerr"></a><a name="cerr"></a>塞勒

`cerr` 物件會控制對與 `stderr` 物件 (在 \<cstdio> 中宣告) 關聯之資料流緩衝區的輸出。

```cpp
extern ostream cerr;
```

#### <a name="return-value"></a>傳回值

[ostream](../standard-library/ostream-typedefs.md#ostream) 物件。

#### <a name="remarks"></a>備註

此物件可控制以位元組資料流形式對標準錯誤輸出進行的未緩衝插入。 建構完物件之後，`cerr.`[flags](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) 運算式就不為零，且 `cerr.tie() == &cout`。

#### <a name="example"></a>範例

```cpp
// iostream_cerr.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

using namespace std;

void TestWide( )
{
   int i = 0;
   wcout << L"Enter a number: ";
   wcin >> i;
   wcerr << L"test for wcerr" << endl;
   wclog << L"test for wclog" << endl;
}

int main( )
{
   int i = 0;
   cout << "Enter a number: ";
   cin >> i;
   cerr << "test for cerr" << endl;
   clog << "test for clog" << endl;
   TestWide( );
}
```

### <a name="cin"></a><a name="cin"></a>Cin

指定 `cin` 全域資料流。

```cpp
extern istream cin;
```

#### <a name="return-value"></a>傳回值

[istream](../standard-library/istream-typedefs.md#istream) 物件。

#### <a name="remarks"></a>備註

此物件可控制以位元組資料流形式從標準輸出進行的擷取。 建構完物件之後，`cin.`[tie](../standard-library/basic-ios-class.md#tie) 呼叫會傳回 `&`[cout](#cout)。

#### <a name="example"></a>範例

這個選項,`cin`在流遇到非數字字元時設定失敗位。 程式清除失敗位,並從流中剝離無效字元以繼續。

```cpp
// iostream_cin.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main()
{
   int x;
   cout << "enter choice:";
   cin >> x;
   while (x < 1 || x > 4)
   {
      cout << "Invalid choice, try again:";
      cin >> x;
      // not a numeric character, probably
      // clear the failure and pull off the non-numeric character
      if (cin.fail())
      {
         cin.clear();
         char c;
         cin >> c;
      }
   }
}
```

```Output
2
```

### <a name="clog"></a><a name="clog"></a>堵塞

指定 `clog` 全域資料流。

```cpp
extern ostream clog;
```

#### <a name="return-value"></a>傳回值

[ostream](../standard-library/ostream-typedefs.md#ostream) 物件。

#### <a name="remarks"></a>備註

此物件可控制以位元組資料流形式對標準錯誤輸出進行的已緩衝插入。

#### <a name="example"></a>範例

如需使用 `clog` 的範例，請參閱 [cerr](#cerr)。

### <a name="cout"></a><a name="cout"></a>cout

指定 `cout` 全域資料流。

```cpp
extern ostream cout;
```

#### <a name="return-value"></a>傳回值

[ostream](../standard-library/ostream-typedefs.md#ostream) 物件。

#### <a name="remarks"></a>備註

此物件可以位元組資料流形式對標準輸出進行的插入。

#### <a name="example"></a>範例

如需使用 `cout` 的範例，請參閱 [cerr](#cerr)。

### <a name="wcerr"></a><a name="wcerr"></a>wcerr

指定 `wcerr` 全域資料流。

```cpp
extern wostream wcerr;
```

#### <a name="return-value"></a>傳回值

[wostream](../standard-library/ostream-typedefs.md#wostream) 物件。

#### <a name="remarks"></a>備註

此物件可控制以寬資料流形式對標準錯誤輸出進行的未緩衝插入。 建構完物件之後，`wcerr.`[flags](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) 運算式就不為零。

#### <a name="example"></a>範例

如需使用 `wcerr` 的範例，請參閱 [cerr](#cerr)。

### <a name="wcin"></a><a name="wcin"></a>wc因

指定 `wcin` 全域資料流。

```cpp
extern wistream wcin;
```

#### <a name="return-value"></a>傳回值

[wistream](../standard-library/istream-typedefs.md#wistream) 物件。

#### <a name="remarks"></a>備註

此物件可控制以寬資料流形式從標準輸出進行的擷取。 建構完物件之後，`wcin.`[tie](../standard-library/basic-ios-class.md#tie) 呼叫會傳回 `&`[wcout](#wcout)。

#### <a name="example"></a>範例

如需使用 `wcin` 的範例，請參閱 [cerr](#cerr)。

### <a name="wclog"></a><a name="wclog"></a>wclog

指定 `wclog` 全域資料流。

```cpp
extern wostream wclog;
```

#### <a name="return-value"></a>傳回值

[wostream](../standard-library/ostream-typedefs.md#wostream) 物件。

#### <a name="remarks"></a>備註

此物件可控制以寬資料流形式對標準錯誤輸出進行的已緩衝插入。

#### <a name="example"></a>範例

如需使用 `wclog` 的範例，請參閱 [cerr](#cerr)。

### <a name="wcout"></a><a name="wcout"></a>wcout

指定 `wcout` 全域資料流。

```cpp
extern wostream wcout;
```

#### <a name="return-value"></a>傳回值

[wostream](../standard-library/ostream-typedefs.md#wostream) 物件。

#### <a name="remarks"></a>備註

此物件能控制插入標準輸出做為寬資料流的作業。

#### <a name="example"></a>範例

如需使用 `wcout` 的範例，請參閱 [cerr](#cerr)。

`wcout` 陳述式中的 `CString` 執行個體必須轉換成 `const wchar_t*`，如下列範例所示。

```cpp
CString cs("meow");

wcout <<(const wchar_t*) cs <<endl;
```

如需詳細資訊，請參閱[基本 CString 運算](../atl-mfc-shared/basic-cstring-operations.md)。

## <a name="see-also"></a>另請參閱

[標題檔案參考](../standard-library/cpp-standard-library-header-files.md)\
[C++標準庫中的線程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[電流程式設計](../standard-library/iostream-programming.md)\
[iostream 慣例](../standard-library/iostreams-conventions.md)
