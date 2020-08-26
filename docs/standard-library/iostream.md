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
ms.openlocfilehash: 5805d441b4fc2fc2927b57f4d94ba8b8ccecb22a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845467"
---
# <a name="ltiostreamgt"></a>&lt;iostream&gt;

宣告對標準資料流的讀取和寫入進行控制的物件。 這通常是您從 c + + 程式進行輸入和輸出時唯一需要的標頭。

## <a name="syntax"></a>語法

```cpp
#include <iostream>
```

> [!NOTE]
> 連結 \<iostream> 庫會使用 `#include <ios>` 、 `#include <streambuf>` 、 `#include <istream>` 和 `#include <ostream>` 語句。

## <a name="remarks"></a>備註

這些物件可分為兩個群組：

- [cin](#cin)、 [cout](#cout)、 [cerr](#cerr)和 [堵塞](#clog) 是位元組導向的，可進行傳統的每次位元組傳輸。

- [wcin](#wcin)、[wcout](#wcout)、[wcerr](#wcerr) 及 [wclog](#wclog) 是寬字元導向物件，會對程式在內部操作的寬字元進行雙向轉譯。

當您對資料流程進行某些作業（例如標準輸入）時，您無法在相同資料流程上進行不同方向的作業。 因此，例如，程式無法在 [cin](#cin) 和 [wcin](#wcin)上交換。

在此標頭中宣告的所有物件都會共用什麼嗎屬性，您可以假設它們是在您定義的任何靜態物件之前（在包含的轉譯單位中）所構成 \<iostream> 。 同樣地，您可以假設在您定義的任何這類靜態物件的析構程式之前，不會終結這些物件。 不過， (輸出資料流程會在程式終止期間進行排清。 ) 因此，您可以在程式啟動和程式終止之後，安全地讀取或寫入標準資料流程。

不過，這種保證不是通用的。 靜態建構函式可能會在另一個轉譯單位中呼叫函式。 呼叫的函式不能假設在此標頭中宣告的物件是以不確定的順序參與靜態結構，而是已建立的。 若要在這類內容中使用這些物件，您必須先建構 [ios_base::Init](../standard-library/ios-base-class.md#init) 類別的物件。

### <a name="global-stream-objects"></a>全域資料流物件

|名稱|描述|
|-|-|
|[cerr](#cerr)|指定 `cerr` 全域資料流。|
|[Cin](#cin)|指定 `cin` 全域資料流。|
|[堵塞](#clog)|指定 `clog` 全域資料流。|
|[cout](#cout)|指定 `cout` 全域資料流。|
|[wcerr](#wcerr)|指定 `wcerr` 全域資料流。|
|[wcin](#wcin)|指定 `wcin` 全域資料流。|
|[wclog](#wclog)|指定 `wclog` 全域資料流。|
|[wcout](#wcout)|指定 `wcout` 全域資料流。|

### <a name="cerr"></a><a name="cerr"></a> cerr

物件會 `cerr` 控制與物件相關聯之資料流程緩衝區的輸出，此物件是 `stderr` 在中宣告 \<cstdio> 。

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

### <a name="cin"></a><a name="cin"></a> Cin

指定 `cin` 全域資料流。

```cpp
extern istream cin;
```

#### <a name="return-value"></a>傳回值

[istream](../standard-library/istream-typedefs.md#istream) 物件。

#### <a name="remarks"></a>備註

此物件可控制以位元組資料流形式從標準輸出進行的擷取。 建構完物件之後，`cin.`[tie](../standard-library/basic-ios-class.md#tie) 呼叫會傳回 `&`[cout](#cout)。

#### <a name="example"></a>範例

在此範例中，會在 `cin` 資料流程的非數值字元之間設定失敗位。 程式會清除失敗位，並從資料流程中移除不正確字元以繼續。

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

### <a name="clog"></a><a name="clog"></a> 堵塞

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

### <a name="cout"></a><a name="cout"></a> cout

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

### <a name="wcerr"></a><a name="wcerr"></a> wcerr

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

### <a name="wcin"></a><a name="wcin"></a> wcin

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

### <a name="wclog"></a><a name="wclog"></a> wclog

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

### <a name="wcout"></a><a name="wcout"></a> wcout

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

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostreams 慣例](../standard-library/iostreams-conventions.md)
