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
ms.openlocfilehash: fa90a861194275d8c82a407e2ca8db6e757aab35
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245234"
---
# <a name="ltiostreamgt"></a>&lt;iostream&gt;

宣告對標準資料流的讀取和寫入進行控制的物件。 包括通常是唯一的標頭，您需要執行輸入和輸出C++程式。

## <a name="syntax"></a>語法

```cpp
#include <iostream>
```

> [!NOTE]
> \<Iostream > 程式庫會使用`#include <ios>`， `#include <streambuf>`， `#include <istream>`，和`#include <ostream>`陳述式。

## <a name="remarks"></a>備註

這些物件可分為兩個群組：

- [cin](#cin)， [cout](#cout)， [cerr](#cerr)，和[clog](#clog)屬於位元組導向，傳統的位元組-一次傳輸作業的執行。

- [wcin](#wcin)、[wcout](#wcout)、[wcerr](#wcerr) 及 [wclog](#wclog) 是寬字元導向物件，會對程式在內部操作的寬字元進行雙向轉譯。

一旦您執行特定作業時，請在資料流，例如標準輸入中，您無法執行相同的資料流上不同方向的作業。 因此，程式無法對兩者[cin](#cin)並[wcin](#wcin)，例如。

宣告在此標頭共用特定屬性的所有物件，您可以假設它們您定義包含在轉譯單位中的任何靜態物件之前建構\<iostream >。 同樣地，您可以假設，這些物件不您定義任何這類靜態物件的解構函式之前終結。 (但輸出資料流會在程式終止期間排清。)因此，在程式啟動之前和程式終止之後，您可以安全地讀取或寫入標準資料流。

這項保證並非通用，不過。 靜態建構函式可能會在另一個轉譯單位中呼叫函式。 呼叫的函式不能假設，已指定轉譯單位參與靜態建構的順序並不確定建構此標頭中宣告的物件。 若要在這類內容中使用這些物件，您必須先建構 [ios_base::Init](../standard-library/ios-base-class.md#init) 類別的物件。

### <a name="global-stream-objects"></a>全域資料流物件

|||
|-|-|
|[cerr](#cerr)|指定 `cerr` 全域資料流。|
|[cin](#cin)|指定 `cin` 全域資料流。|
|[clog](#clog)|指定 `clog` 全域資料流。|
|[cout](#cout)|指定 `cout` 全域資料流。|
|[wcerr](#wcerr)|指定 `wcerr` 全域資料流。|
|[wcin](#wcin)|指定 `wcin` 全域資料流。|
|[wclog](#wclog)|指定 `wclog` 全域資料流。|
|[wcout](#wcout)|指定 `wcout` 全域資料流。|

###  <a name="cerr"></a> cerr

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

###  <a name="cin"></a> cin

指定 `cin` 全域資料流。

```cpp
extern istream cin;
```

#### <a name="return-value"></a>傳回值

[istream](../standard-library/istream-typedefs.md#istream) 物件。

#### <a name="remarks"></a>備註

此物件可控制以位元組資料流形式從標準輸出進行的擷取。 建構完物件之後，`cin.`[tie](../standard-library/basic-ios-class.md#tie) 呼叫會傳回 `&`[cout](#cout)。

#### <a name="example"></a>範例

在此範例中，`cin`設定失敗位元資料流上跨非數字字元時。 清除失敗位元程式，並去除無效的字元，從繼續資料流。

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

###  <a name="clog"></a> clog

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

###  <a name="cout"></a> cout

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

### <a name="wcerr"></a> wcerr

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

### <a name="wcin"></a> wcin

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

### <a name="wclog"></a> wclog

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

### <a name="wcout"></a> wcout

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

```
CString cs("meow");

wcout <<(const wchar_t*) cs <<endl;
```

如需詳細資訊，請參閱[基本 CString 運算](../atl-mfc-shared/basic-cstring-operations.md)。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 程式設計](../standard-library/iostream-programming.md)<br/>
[iostream 慣例](../standard-library/iostreams-conventions.md)<br/>
