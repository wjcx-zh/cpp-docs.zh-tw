---
title: '&lt;iostream&gt; | Microsoft Docs'
ms.custom: 
ms.date: 09/20/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords: iostream header
ms.assetid: de5d39e1-7e77-4b55-bcd1-7c77b41515c8
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 430981da5ec304bf832e759d40870ee88f3e6557
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ltiostreamgt"></a>&lt;iostream&gt;
宣告對標準資料流的讀取和寫入進行控制的物件。 這通常是您從 C++ 程式中執行輸入和輸出時唯一需要納入的標頭。  
  
## <a name="syntax"></a>語法  
  
```  
#include <iostream>  
  
```  
  
## <a name="remarks"></a>備註  
 這些物件可分為兩個群組：  
  
- [cin](#cin)、[cout](#cout)、[cerr](#cerr) 及 [clog](#clog) 是位元組導向物件，會執行傳統一次一個位元組的傳輸。  
  
- [wcin](#wcin)、[wcout](#wcout)、[wcerr](#wcerr) 及 [wclog](#wclog) 是寬字元導向物件，會對程式在內部操作的寬字元進行雙向轉譯。  
  
 在您對資料流執行特定作業後 (例如標準輸入)，您無法對相同的資料流執行不同方向的作業。 因此，舉例來說，程式無法對 [cin](#cin) 和 [wcin](#wcin) 進行互換操作。  
  
 在此標頭中宣告的所有物件會共用特定屬性 — 您可以假設這些物件是在您所定義的任何靜態物件之前，於包含 \<iostream> 的轉譯單位中建構的。 同樣地，您可以假設這類物件不會在您定義的任何此類靜態物件的解構函式之前終結。 (但輸出資料流會在程式終止期間排清。)因此，在程式啟動之前和程式終止之後，您可以安全地讀取或寫入標準資料流。  
  
 但這項保證並非一體適用。 靜態建構函式可能會在另一個轉譯單位中呼叫函式。 由於轉譯單位參與靜態建構的順序並不確定，呼叫的函式無法假設在此標頭中宣告的物件已建構。 若要在這類內容中使用這些物件，您必須先建構 [ios_base::Init](../standard-library/ios-base-class.md#init) 類別的物件。  
  
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
  
###  <a name="cerr"></a>  cerr  
 `cerr` 物件會控制對與 `stderr` 物件 (在 \<cstdio> 中宣告) 關聯之資料流緩衝區的輸出。  
  
```  
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
  
###  <a name="cin"></a>  cin  
 指定 `cin` 全域資料流。  
  
```  
extern istream cin;  
```  
  
#### <a name="return-value"></a>傳回值  
 [istream](../standard-library/istream-typedefs.md#istream) 物件。  
  
#### <a name="remarks"></a>備註  
 此物件可控制以位元組資料流形式從標準輸出進行的擷取。 建構完物件之後，`cin.`[tie](../standard-library/basic-ios-class.md#tie) 呼叫會傳回 `&`[cout](#cout)。  
  
#### <a name="example"></a>範例  
  在此範例中，`cin` 會在遇到非數字字元時，在資料流上設定失敗位元。 此程式會清除失敗位元，並從資料流中刪除無效字元以繼續作業。  
  
```  
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
  
###  <a name="clog"></a>  clog  
 指定 `clog` 全域資料流。  
  
```  
extern ostream clog;  
```  
  
#### <a name="return-value"></a>傳回值  
 [ostream](../standard-library/ostream-typedefs.md#ostream) 物件。  
  
#### <a name="remarks"></a>備註  
 此物件可控制以位元組資料流形式對標準錯誤輸出進行的已緩衝插入。  
  
#### <a name="example"></a>範例  
  如需使用 `clog` 的範例，請參閱 [cerr](#cerr)。  
  
###  <a name="cout"></a>  cout  
 指定 `cout` 全域資料流。  
  
```  
extern ostream cout;  
```  
  
#### <a name="return-value"></a>傳回值  
 [ostream](../standard-library/ostream-typedefs.md#ostream) 物件。  
  
#### <a name="remarks"></a>備註  
 此物件可以位元組資料流形式對標準輸出進行的插入。  
  
#### <a name="example"></a>範例  
  如需使用 `cout` 的範例，請參閱 [cerr](#cerr)。  
  
###  <a name="wcerr"></a>  wcerr  
 指定 `wcerr` 全域資料流。  
  
```  
extern wostream wcerr;  
```  
  
#### <a name="return-value"></a>傳回值  
 [wostream](../standard-library/ostream-typedefs.md#wostream) 物件。  
  
#### <a name="remarks"></a>備註  
 此物件可控制以寬資料流形式對標準錯誤輸出進行的未緩衝插入。 建構完物件之後，`wcerr.`[flags](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) 運算式就不為零。  
  
#### <a name="example"></a>範例  
  如需使用 `wcerr` 的範例，請參閱 [cerr](#cerr)。  
  
###  <a name="wcin"></a>  wcin  
 指定 `wcin` 全域資料流。  
  
```  
extern wistream wcin;  
```  
  
#### <a name="return-value"></a>傳回值  
 [wistream](../standard-library/istream-typedefs.md#wistream) 物件。  
  
#### <a name="remarks"></a>備註  
 此物件可控制以寬資料流形式從標準輸出進行的擷取。 建構完物件之後，`wcin.`[tie](../standard-library/basic-ios-class.md#tie) 呼叫會傳回 `&`[wcout](#wcout)。  
  
#### <a name="example"></a>範例  
  如需使用 `wcin` 的範例，請參閱 [cerr](#cerr)。  
  
###  <a name="wclog"></a>  wclog  
 指定 `wclog` 全域資料流。  
  
```  
extern wostream wclog;  
```  
  
#### <a name="return-value"></a>傳回值  
 [wostream](../standard-library/ostream-typedefs.md#wostream) 物件。  
  
#### <a name="remarks"></a>備註  
 此物件可控制以寬資料流形式對標準錯誤輸出進行的已緩衝插入。  
  
#### <a name="example"></a>範例  
  如需使用 `wclog` 的範例，請參閱 [cerr](#cerr)。  
  
###  <a name="wcout"></a>  wcout  
 指定 `wcout` 全域資料流。  
  
```  
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
  
## <a name="see-also"></a>請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostream 慣例](../standard-library/iostreams-conventions.md)

