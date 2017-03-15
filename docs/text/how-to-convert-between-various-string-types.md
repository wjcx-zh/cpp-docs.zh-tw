---
title: "如何：在各種字串類型之間轉換 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "轉換字串類型"
  - "字串轉換 [C++]"
  - "字串 [C++], 轉換"
ms.assetid: e7e4f741-3c82-45f0-b8c0-1e1e343b0e77
caps.latest.revision: 13
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 13
---
# 如何：在各種字串類型之間轉換
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個主題示範如何將各種 Visual C\+\+ 字串型別轉換成其他字串。  可以進行轉換的字串型別包括 `char *`、`wchar_t*`、[\_bstr\_t](../cpp/bstr-t-class.md)、[CComBSTR](../atl/reference/ccombstr-class.md)、[CString](../atl-mfc-shared/using-cstring.md)、[basic\_string](../standard-library/basic-string-class.md) 以及 <xref:System.String?displayProperty=fullName>。  在所有情況下，當某字串轉換成新的型別時，都會產生該字串的複本。  對新的字串所做的任何變更，都不會影響原來的字串，反之亦然。  
  
## 從 char \* 轉換  
  
## 範例  
  
### 說明  
 這個範例中，會示範如何從 `char *` 轉換成上列的其他字串型別。  `char *` 字串 \(也稱為 C Style 字串\) 會使用 null 字元表示字串結尾。  C Style 字串通常每個字元需要一個位元組，但也可以使用兩個位元組。  在下列範例中，由於從 Unicode 字串進行轉換所產生的字串資料，`char *` 字串有時候也稱為多位元組字元字串。  單位元組和多位元組字元 \(`MBCS`\) 函式對於 `char *` 字串都可以運作。  
  
### 程式碼  
  
```  
// convert_from_char.cpp  
// compile with: /clr /link comsuppw.lib  
  
#include <iostream>  
#include <stdlib.h>  
#include <string>  
  
#include "atlbase.h"  
#include "atlstr.h"  
#include "comutil.h"  
  
using namespace std;  
using namespace System;  
  
int main()  
{  
    // Create and display a C style string, and then use it   
    // to create different kinds of strings.  
    char *orig = "Hello, World!";  
    cout << orig << " (char *)" << endl;  
  
    // newsize describes the length of the   
    // wchar_t string called wcstring in terms of the number   
    // of wide characters, not the number of bytes.  
    size_t newsize = strlen(orig) + 1;  
  
    // The following creates a buffer large enough to contain   
    // the exact number of characters in the original string  
    // in the new format. If you want to add more characters  
    // to the end of the string, increase the value of newsize  
    // to increase the size of the buffer.  
    wchar_t * wcstring = new wchar_t[newsize];  
  
    // Convert char* string to a wchar_t* string.  
    size_t convertedChars = 0;  
    mbstowcs_s(&convertedChars, wcstring, newsize, orig, _TRUNCATE);  
    // Display the result and indicate the type of string that it is.  
    wcout << wcstring << _T(" (wchar_t *)") << endl;  
  
    // Convert the C style string to a _bstr_t string.  
    _bstr_t bstrt(orig);  
    // Append the type of string to the new string  
    // and then display the result.  
    bstrt += " (_bstr_t)";  
    cout << bstrt << endl;  
  
    // Convert the C style string to a CComBSTR string.  
    CComBSTR ccombstr(orig);  
    if (ccombstr.Append(_T(" (CComBSTR)")) == S_OK)  
    {  
        CW2A printstr(ccombstr);  
        cout << printstr << endl;  
    }  
  
    // Convert the C style string to a CstringA and display it.  
    CStringA cstringa(orig);  
    cstringa += " (CStringA)";  
    cout << cstringa << endl;  
  
    // Convert the C style string to a CStringW and display it.  
    CStringW cstring(orig);  
    cstring += " (CStringW)";  
    // To display a CStringW correctly, use wcout and cast cstring  
    // to (LPCTSTR).  
    wcout << (LPCTSTR)cstring << endl;  
  
    // Convert the C style string to a basic_string and display it.  
    string basicstring(orig);  
    basicstring += " (basic_string)";  
    cout << basicstring << endl;  
  
    // Convert the C style string to a System::String and display it.  
    String ^systemstring = gcnew String(orig);  
    systemstring += " (System::String)";  
    Console::WriteLine("{0}", systemstring);  
    delete systemstring;  
}  
```  
  
### Output  
  
```  
Hello, World! (char *)  
Hello, World! (wchar_t *)  
Hello, World! (_bstr_t)  
Hello, World! (CComBSTR)  
Hello, World! (CStringA)  
Hello, World! (CStringW)  
Hello, World! (basic_string)  
Hello, World! (System::String)  
```  
  
## 從 wchar\_t \* 轉換  
  
## 範例  
  
### 說明  
 這個範例中，會示範如何從 `wchar_t *` 轉換成上列的其他字串型別。  有些字串型別 \(包括 `wchar_t *`\) 會實作寬字元格式。  若要在多位元組和寬字元格式之間轉換字串，可以使用單一函式呼叫 \(例如 `mbstowcs_s`\) 或類別的建構函式引動過程 \(例如 `CStringA`\)。  
  
### 程式碼  
  
```  
// convert_from_wchar_t.cpp  
// compile with: /clr /link comsuppw.lib  
  
#include <iostream>  
#include <stdlib.h>  
#include <string>  
  
#include "atlbase.h"  
#include "atlstr.h"  
#include "comutil.h"  
  
using namespace std;  
using namespace System;  
  
int main()  
{  
    // Create a string of wide characters, display it, and then  
    // use this string to create other types of strings.  
    wchar_t *orig = _T("Hello, World!");  
    wcout << orig << _T(" (wchar_t *)") << endl;  
  
    // Convert the wchar_t string to a char* string. Record   
    //.the length of the original string and add 1 to it to  
    //.account for the terminating null character.  
    size_t origsize = wcslen(orig) + 1;  
    size_t convertedChars = 0;  
  
    // Use a multibyte string to append the type of string  
    // to the new string before displaying the result.  
    char strConcat[] = " (char *)";  
    size_t strConcatsize = (strlen( strConcat ) + 1)*2;  
  
    // Allocate two bytes in the multibyte output string for every wide  
    // character in the input string (including a wide character  
    // null). Because a multibyte character can be one or two bytes,  
    // you should allot two bytes for each character. Having extra  
    // space for the new string is not an error, but having  
    // insufficient space is a potential security problem.  
    const size_t newsize = origsize*2;  
    // The new string will contain a converted copy of the original  
    // string plus the type of string appended to it.  
    char *nstring = new char[newsize+strConcatsize];  
  
    // Put a copy of the converted string into nstring  
    wcstombs_s(&convertedChars, nstring, newsize, orig, _TRUNCATE);  
    // append the type of string to the new string.  
    _mbscat_s((unsigned char*)nstring, newsize+strConcatsize, (unsigned char*)strConcat);  
    // Display the result.  
    cout << nstring << endl;  
  
    // Convert a wchar_t to a _bstr_t string and display it.  
    _bstr_t bstrt(orig);  
    bstrt += " (_bstr_t)";  
    cout << bstrt << endl;  
  
    // Convert the wchar_t string to a BSTR wide character string   
    // by using the ATL CComBSTR wrapper class for BSTR strings.  
    // Then display the result.  
  
    CComBSTR ccombstr(orig);  
    if (ccombstr.Append(_T(" (CComBSTR)")) == S_OK)  
    {  
        // CW2A converts the string in ccombstr to a multibyte   
        // string in printstr, used here for display output.  
        CW2A printstr(ccombstr);  
        cout << printstr << endl;  
        // The following line of code is an easier way to  
        // display wide character strings:  
        // wcout << (LPCTSTR) ccombstr << endl;  
    }  
  
    // Convert a wide wchar_t string to a multibyte CStringA,  
    // append the type of string to it, and display the result.  
    CStringA cstringa(orig);  
    cstringa += " (CStringA)";  
    cout << cstringa << endl;  
  
    // Convert a wide character wchar_t string to a wide  
    // character CStringW string and append the type of string to it  
    CStringW cstring(orig);  
    cstring += " (CStringW)";  
    // To display a CStringW correctly, use wcout and cast cstring  
    // to (LPCTSTR).  
    wcout << (LPCTSTR)cstring << endl;  
  
    // Convert the wide character wchar_t string to a  
    // basic_string, append the type of string to it, and  
    // display the result.  
    wstring basicstring(orig);  
    basicstring += _T(" (basic_string)");  
    wcout << basicstring << endl;  
  
    // Convert a wide character wchar_t string to a   
    // System::String string, append the type of string to it,  
    // and display the result.  
    String ^systemstring = gcnew String(orig);  
    systemstring += " (System::String)";  
    Console::WriteLine("{0}", systemstring);  
    delete systemstring;  
}  
```  
  
### Output  
  
```  
Hello, World! (wchar_t *)  
Hello, World! (char *)  
Hello, World! (_bstr_t)  
Hello, World! (CComBSTR)  
Hello, World! (CStringA)  
Hello, World! (CStringW)  
Hello, World! (basic_string)  
Hello, World! (System::String)  
```  
  
## 從 \_bstr\_t 轉換  
  
## 範例  
  
### 說明  
 這個範例中，會示範如何從 `_bstr_t` 轉換成上列的其他字串型別。  `_bstr_t` 物件可以用來封裝寬字元 `BSTR` 字串。  BSTR 字串具有長度值，且不使用 Null 字元來結束字串，但做為轉換目標的字串型別可能需要代表結束的 Null。  
  
### 程式碼  
  
```  
// convert_from_bstr_t.cpp  
// compile with: /clr /link comsuppw.lib  
  
#include <iostream>  
#include <stdlib.h>  
#include <string>  
  
#include "atlbase.h"  
#include "atlstr.h"  
#include "comutil.h"  
  
using namespace std;  
using namespace System;  
  
int main()  
{  
    // Create a _bstr_t string, display the result, and indicate the  
    // type of string that it is.  
    _bstr_t orig("Hello, World!");  
    wcout << orig << " (_bstr_t)" << endl;  
  
    // Convert the wide character _bstr_t string to a C style  
    // string. To be safe, allocate two bytes for each character  
    // in the char* string, including the terminating null.  
    const size_t newsize = (orig.length()+1)*2;  
    char *nstring = new char[newsize];  
  
    // Uses the _bstr_t operator (char *) to obtain a null   
    // terminated string from the _bstr_t object for  
    // nstring.  
    strcpy_s(nstring, newsize, (char *)orig);  
    strcat_s(nstring, newsize, " (char *)");  
    cout << nstring << endl;  
  
    // Prepare the type of string to append to the result.  
    wchar_t strConcat[] = _T(" (wchar_t *)");  
    size_t strConcatLen = wcslen(strConcat) + 1;  
  
    // Convert a _bstr_t to a wchar_t* string.  
    const size_t widesize = orig.length()+ strConcatLen;  
    wchar_t *wcstring = new wchar_t[newsize];  
    wcscpy_s(wcstring, widesize, (wchar_t *)orig);  
    wcscat_s(wcstring, widesize, strConcat);  
    wcout << wcstring << endl;  
  
    // Convert a _bstr_t string to a CComBSTR string.  
    CComBSTR ccombstr((char *)orig);  
    if (ccombstr.Append(_T(" (CComBSTR)")) == S_OK)  
    {  
        CW2A printstr(ccombstr);  
        cout << printstr << endl;  
    }  
  
    // Convert a _bstr_t to a CStringA string.  
    CStringA cstringa(orig.GetBSTR());  
    cstringa += " (CStringA)";  
    cout << cstringa << endl;  
  
    // Convert a _bstr_t to a CStringW string.  
    CStringW cstring(orig.GetBSTR());  
    cstring += " (CStringW)";  
    // To display a cstring correctly, use wcout and  
    // "cast" the cstring to (LPCTSTR).  
    wcout << (LPCTSTR)cstring << endl;  
  
    // Convert the _bstr_t to a basic_string.  
    string basicstring((char *)orig);  
    basicstring += " (basic_string)";  
    cout << basicstring << endl;  
  
    // Convert the _bstr_t to a System::String.  
    String ^systemstring = gcnew String((char *)orig);  
    systemstring += " (System::String)";  
    Console::WriteLine("{0}", systemstring);  
    delete systemstring;  
}  
```  
  
### Output  
  
```  
Hello, World! (_bstr_t)  
Hello, World! (char *)  
Hello, World! (wchar_t *)  
Hello, World! (CComBSTR)  
Hello, World! (CStringA)  
Hello, World! (CStringW)  
Hello, World! (basic_string)  
Hello, World! (System::String)  
```  
  
## 從 CComBSTR 轉換  
  
## 範例  
  
### 說明  
 這個範例中，會示範如何從 `CComBSTR` 轉換成上列的其他字串型別。  與 \_bstr\_t 類似，`CComBSTR` 物件可以用來封裝寬字元 BSTR 字串。  BSTR 字串具有長度值，且不使用 Null 字元來結束字串，但做為轉換目標的字串型別可能需要代表結束的 Null。  
  
### 程式碼  
  
```  
// convert_from_ccombstr.cpp  
// compile with: /clr /link comsuppw.lib  
  
#include <iostream>  
#include <stdlib.h>  
#include <string>  
  
#include "atlbase.h"  
#include "atlstr.h"  
#include "comutil.h"  
#include "vcclr.h"  
  
using namespace std;  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
int main()  
{  
    // Create and initialize a BSTR string by using a CComBSTR object.  
    CComBSTR orig("Hello, World!");  
    // Convert the BSTR into a multibyte string, display the result,  
    // and indicate the type of string that it is.  
    CW2A printstr(orig);  
    cout << printstr << " (CComBSTR)" << endl;  
  
    // Convert a wide character CComBSTR string to a  
    // regular multibyte char* string. Allocate enough space  
    // in the new string for the largest possible result,  
    // including space for a terminating null.  
    const size_t newsize = (orig.Length()+1)*2;  
    char *nstring = new char[newsize];  
  
    // Create a string conversion object, copy the result to  
    // the new char* string, and display the result.  
    CW2A tmpstr1(orig);  
    strcpy_s(nstring, newsize, tmpstr1);  
    cout << nstring << " (char *)" << endl;  
  
    // Prepare the type of string to append to the result.  
    wchar_t strConcat[] = _T(" (wchar_t *)");  
    size_t strConcatLen = wcslen(strConcat) + 1;  
  
    // Convert a wide character CComBSTR string to a wchar_t*.  
    // The code first determines the length of the converted string  
    // plus the length of the appended type of string, then  
    // prepares the final wchar_t string for display.  
    const size_t widesize = orig.Length()+ strConcatLen;  
    wchar_t *wcstring = new wchar_t[widesize];  
    wcscpy_s(wcstring, widesize, orig);  
    wcscat_s(wcstring, widesize, strConcat);  
  
    // Display the result. Unlike CStringW, a wchar_t does not need  
    // a cast to (LPCTSTR) with wcout.  
    wcout << wcstring << endl;  
  
    // Convert a wide character CComBSTR to a wide character _bstr_t,  
    // append the type of string to it, and display the result.  
    _bstr_t bstrt(orig);  
    bstrt += " (_bstr_t)";  
    cout << bstrt << endl;  
  
    // Convert a wide character CComBSTR to a multibyte CStringA,  
    // append the type of string to it, and display the result.  
    CStringA cstringa(orig);  
    cstringa += " (CStringA)";  
    cout << cstringa << endl;  
  
    // Convert a wide character CComBSTR to a wide character CStringW.  
    CStringW cstring(orig);  
    cstring += " (CStringW)";  
    // To display a cstring correctly, use wcout and cast cstring  
    // to (LPCTSTR).  
    wcout << (LPCTSTR)cstring << endl;  
  
    // Convert a wide character CComBSTR to a wide character   
    // basic_string.  
    wstring basicstring(orig);  
    basicstring += _T(" (basic_string)");  
    wcout << basicstring << endl;  
  
    // Convert a wide character CComBSTR to a System::String.  
    String ^systemstring = gcnew String(orig);  
    systemstring += " (System::String)";  
    Console::WriteLine("{0}", systemstring);  
    delete systemstring;  
}  
```  
  
### Output  
  
```  
Hello, World! (CComBSTR)  
Hello, World! (char *)  
Hello, World! (wchar_t *)  
Hello, World! (_bstr_t)  
Hello, World! (CStringA)  
Hello, World! (CStringW)  
Hello, World! (basic_string)  
Hello, World! (System::String)  
```  
  
## 從 CString 轉換  
  
## 範例  
  
### 說明  
 這個範例中，會示範如何從 `CString` 轉換成上列的其他字串型別。  `CString` 是以 TCHAR 資料型別為基礎，因此需根據符號 `_UNICODE` 有否定義而定。  如果未定義 `_UNICODE`，`TCHAR` 就會定義為 char 而 `CString` 包含多位元組字元字串；如果有定義 `_UNICODE`，則 `TCHAR` 會定義為 `wchar_t` 而 `CString` 包含寬字元字串。  
  
 `CStringA` 是一律多位元組字串版本的 `CString`，`CStringW` 則是僅限寬字元字串的版本。  `CStringA` 和 `CStringW` 都不會使用 `_UNICODE` 來判斷應該如何編譯。  本範例中使用 `CStringA` 和 `CStringW` 來釐清緩衝區大小配置及輸出處理中的細微差異。  
  
### 程式碼  
  
```  
// convert_from_cstring.cpp  
// compile with: /clr /link comsuppw.lib  
  
#include <iostream>  
#include <stdlib.h>  
#include <string>  
  
#include "atlbase.h"  
#include "atlstr.h"  
#include "comutil.h"  
  
using namespace std;  
using namespace System;  
  
int main()  
{  
    // Set up a multibyte CStringA string.  
    CStringA origa("Hello, World!");  
    cout << origa << " (CStringA)" << endl;  
```  
  
```  
// Set up a wide character CStringW string.  
CStringW origw("Hello, World!");  
wcout << (LPCTSTR)origw << _T(" (CStringW)") << endl;  
  
// Convert to a char* string from CStringA string   
// and display the result.  
const size_t newsizea = (origa.GetLength() + 1);  
char *nstringa = new char[newsizea];  
strcpy_s(nstringa, newsizea, origa);  
cout << nstringa << " (char *)" << endl;  
  
// Convert to a char* string from a wide character   
// CStringW string. To be safe, we allocate two bytes for each  
// character in the original string, including the terminating  
// null.  
const size_t newsizew = (origw.GetLength() + 1)*2;  
char *nstringw = new char[newsizew];  
size_t convertedCharsw = 0;  
wcstombs_s(&convertedCharsw, nstringw, newsizew, origw, _TRUNCATE );  
cout << nstringw << " (char *)" << endl;  
  
// Convert to a wchar_t* from CStringA  
size_t convertedCharsa = 0;  
wchar_t *wcstring = new wchar_t[newsizea];  
mbstowcs_s(&convertedCharsa, wcstring, newsizea, origa, _TRUNCATE);  
wcout << wcstring << _T(" (wchar_t *)") << endl;  
  
// Convert to a wide character wchar_t* string from   
// a wide character CStringW string.   
wchar_t *n2stringw = new wchar_t[newsizew];  
wcscpy_s( n2stringw, newsizew, origw );  
wcout << n2stringw << _T(" (wchar_t *)") << endl;  
  
// Convert to a wide character _bstr_t string from   
// a multibyte CStringA string.  
_bstr_t bstrt(origa);  
bstrt += _T(" (_bstr_t)");  
wcout << bstrt << endl;  
  
// Convert to a wide character_bstr_t string from   
// a wide character CStringW string.  
bstr_t bstrtw(origw);  
bstrtw += " (_bstr_t)";  
wcout << bstrtw << endl;  
  
// Convert to a wide character CComBSTR string from   
// a multibyte character CStringA string.  
CComBSTR ccombstr(origa);  
if (ccombstr.Append(_T(" (CComBSTR)")) == S_OK)  
{  
    // Convert the wide character string to multibyte  
    // for printing.  
    CW2A printstr(ccombstr);  
    cout << printstr << endl;  
}  
  
// Convert to a wide character CComBSTR string from   
// a wide character CStringW string.  
CComBSTR ccombstrw(origw);  
// Append the type of string to it, and display the result.  
  
if (ccombstrw.Append(_T(" (CComBSTR)")) == S_OK)  
{  
    CW2A printstrw(ccombstrw);  
    wcout << printstrw << endl;  
}  
  
// Convert a multibyte character CStringA to a   
// multibyte version of a basic_string string.  
string basicstring(origa);  
basicstring += " (basic_string)";  
cout << basicstring << endl;  
  
// Convert a wide character CStringW to a   
// wide character version of a basic_string   
// string.  
wstring basicstringw(origw);  
basicstringw += _T(" (basic_string)");  
wcout << basicstringw << endl;  
  
// Convert a multibyte character CStringA to a   
// System::String.  
String ^systemstring = gcnew String(origa);  
systemstring += " (System::String)";  
Console::WriteLine("{0}", systemstring);  
delete systemstring;  
```  
  
```  
    // Convert a wide character CStringW to a   
    // System::String.  
    String ^systemstringw = gcnew String(origw);  
    systemstringw += " (System::String)";  
    Console::WriteLine("{0}", systemstringw);  
    delete systemstringw;  
}  
```  
  
### Output  
  
```  
Hello, World! (CStringA)  
Hello, World! (CStringW)  
Hello, World! (char *)  
Hello, World! (char *)  
Hello, World! (wchar_t *)  
Hello, World! (wchar_t *)  
Hello, World! (_bstr_t)  
Hello, World! (_bstr_t)  
Hello, World! (CComBSTR)  
Hello, World! (CComBSTR)  
Hello, World! (basic_string)  
Hello, World! (System::String)  
```  
  
## 從 basic\_string 轉換  
  
## 範例  
  
### 說明  
 這個範例中，會示範如何從 `basic_string` 轉換成上列的其他字串型別。  
  
### 程式碼  
  
```  
// convert_from_basic_string.cpp  
// compile with: /clr /link comsuppw.lib  
  
#include <iostream>  
#include <stdlib.h>  
#include <string>  
  
#include "atlbase.h"  
#include "atlstr.h"  
#include "comutil.h"  
  
using namespace std;  
using namespace System;  
  
int main()  
{  
    // Set up a basic_string string.  
    string orig("Hello, World!");  
    cout << orig << " (basic_string)" << endl;  
  
    // Convert a wide char basic_string string to a multibyte char*  
    // string. To be safe, we allocate two bytes for each character  
    // in the original string, including the terminating null.  
    const size_t newsize = (strlen(orig.c_str()) + 1)*2;  
    char *nstring = new char[newsize];  
    strcpy_s(nstring, newsize, orig.c_str());  
    cout << nstring << " (char *)" << endl;  
  
    // Convert a basic_string string to a wide character   
    // wchar_t* string. You must first convert to a char*   
    // for this to work.  
    const size_t newsizew = strlen(orig.c_str()) + 1;  
    size_t convertedChars = 0;  
    wchar_t *wcstring = new wchar_t[newsizew];  
    mbstowcs_s(&convertedChars, wcstring, newsizew, orig.c_str(), _TRUNCATE);  
    wcout << wcstring << _T(" (wchar_t *)") << endl;  
  
    // Convert a basic_string string to a wide character   
    // _bstr_t string.   
    _bstr_t bstrt(orig.c_str());  
    bstrt += _T(" (_bstr_t)");  
    wcout << bstrt << endl;  
  
    // Convert a basic_string string to a wide character   
    // CComBSTR string.  
    CComBSTR ccombstr(orig.c_str());  
    if (ccombstr.Append(_T(" (CComBSTR)")) == S_OK)  
    {  
        // Make a multibyte version of the CComBSTR string  
        // and display the result.  
        CW2A printstr(ccombstr);  
        cout << printstr << endl;  
    }  
  
    // Convert a basic_string string into a multibyte   
    // CStringA string.  
    CStringA cstring(orig.c_str());  
    cstring += " (CStringA)";  
    cout << cstring << endl;  
  
    // Convert a basic_string string into a wide   
    // character CStringW string.  
    CStringW cstringw(orig.c_str());  
    cstringw += _T(" (CStringW)");  
    wcout << (LPCTSTR)cstringw << endl;  
  
    // Convert a basic_string string to a System::String  
    String ^systemstring = gcnew String(orig.c_str());  
    systemstring += " (System::String)";  
    Console::WriteLine("{0}", systemstring);  
    delete systemstring;  
}  
```  
  
### Output  
  
```  
Hello, World! (basic_string)  
Hello, World! (char *)  
Hello, World! (wchar_t *)  
Hello, World! (_bstr_t)  
Hello, World! (CComBSTR)  
Hello, World! (CStringA)  
Hello, World! (CStringW)  
Hello, World! (System::String)  
```  
  
## 從 System::String 轉換  
  
## 範例  
  
### 說明  
 這個範例中，會示範如何從寬字元 \(Unicode\) [System::String](assetId:///System::String?qualifyHint=True&autoUpgrade=True) 轉換成上列的其他字串型別。  
  
### 程式碼  
  
```  
// convert_from_system_string.cpp  
// compile with: /clr /link comsuppw.lib  
  
#include <iostream>  
#include <stdlib.h>  
#include <string>  
  
#include "atlbase.h"  
#include "atlstr.h"  
#include "comutil.h"  
#include "vcclr.h"  
  
using namespace std;  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
int main()  
{  
    // Set up a System::String and display the result.  
    String ^orig = gcnew String("Hello, World!");  
    Console::WriteLine("{0} (System::String)", orig);  
  
    // Obtain a pointer to the System::String in order to  
    // first lock memory into place, so that the  
    // Garbage Collector (GC) cannot move that object  
    // while we call native functions.  
    pin_ptr<const wchar_t> wch = PtrToStringChars(orig);  
  
    // Make a copy of the system string as a multibyte  
    // char* string. Allocate two bytes in the multibyte  
    // output string for every wide character in the input  
    // string, including space for a terminating null.  
    size_t origsize = wcslen(wch) + 1;  
    const size_t newsize = origsize*2;  
    size_t convertedChars = 0;  
    char *nstring = new char[newsize];  
    wcstombs_s(&convertedChars, nstring, newsize, wch, _TRUNCATE);  
    cout << nstring << " (char *)" << endl;  
  
    // Convert a wide character system string to a   
    // wide character wchar_t* string.  
    const size_t newsizew = origsize;  
    wchar_t *wcstring = new wchar_t[newsizew];  
    wcscpy_s(wcstring, newsizew, wch);  
    wcout << wcstring << _T(" (wchar_t *)") << endl;  
  
    // Convert a wide character system string to a  
    // wide character _bstr_t string.  
    _bstr_t bstrt(wch);  
    bstrt += " (_bstr_t)";  
    cout << bstrt << endl;  
  
    // Convert a wide character system string   
    // to a wide character CComBSTR string.  
    CComBSTR ccombstr(wch);  
    if (ccombstr.Append(_T(" (CComBSTR)")) == S_OK)  
    {  
        // Make a multibyte copy of the CComBSTR string  
        // and display the result.  
        CW2A printstr(ccombstr);  
        cout << printstr << endl;  
    }  
  
    // Convert a wide character System::String to  
    // a multibyte CStringA string.  
    CStringA cstring(wch);  
    cstring += " (CStringA)";  
    cout << cstring << endl;  
  
    // Convert a wide character System::String to  
    // a wide character CStringW string.  
    CStringW cstringw(wch);  
    cstringw += " (CStringW)";  
    wcout << (LPCTSTR)cstringw << endl;  
  
    // Convert a wide character System::String to   
    // a wide character basic_string.  
    wstring basicstring(wch);  
    basicstring += _T(" (basic_string)");  
    wcout << basicstring << endl;  
  
    delete orig;  
}  
```  
  
### Output  
  
```  
Hello, World! (System::String)  
Hello, World! (char *)  
Hello, World! (wchar_t *)  
Hello, World! (_bstr_t)  
Hello, World! (CComBSTR)  
Hello, World! (CStringA)  
Hello, World! (CStringW)  
Hello, World! (basic_string)  
```  
  
## 請參閱  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/zh-tw/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [ATL and MFC String Conversion Macros](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md)   
 [CString Operations Relating to C\-Style Strings](../atl-mfc-shared/cstring-operations-relating-to-c-style-strings.md)   
 [如何：將標準字串轉換為 System::String](../dotnet/how-to-convert-standard-string-to-system-string.md)   
 [如何：將 System::String 轉換為標準字串](../dotnet/how-to-convert-system-string-to-standard-string.md)   
 [如何：將 System::String 轉換為 wchar\_t\* 或 char\*](../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)   
 [使用 CComBSTR 進行程式設計](../atl/programming-with-ccombstr-atl.md)   
 [mbstowcs\_s、\_mbstowcs\_s\_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)   
 [wcstombs\_s、\_wcstombs\_s\_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)   
 [strcpy\_s、wcscpy\_s、\_mbscpy\_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)   
 [strcat\_s、wcscat\_s、\_mbscat\_s](../c-runtime-library/reference/strcat-s-wcscat-s-mbscat-s.md)   
 [pin\_ptr \(C\+\+\/CLI\)](../windows/pin-ptr-cpp-cli.md)