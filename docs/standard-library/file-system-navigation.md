---
title: 檔案系統巡覽
description: 如何使用C++標準庫文件系統 API 來導航檔案系統。
ms.date: 04/13/2020
ms.assetid: f7cc5f5e-a541-4e00-87c7-a3769ef6096d
ms.openlocfilehash: 412d865582a14da7b8c31d9f07a43106b0c49491
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368433"
---
# <a name="file-system-navigation"></a>檔案系統巡覽

\<filesystem> 標頭會實作 C++ 檔案系統技術規格 ISO/IEC TS 18822:2015 (草案最終版：[ISO/IEC JTC 1/SC 22/WG 21 N4100](https://wg21.link/n4100))，並提供相關類型與函式，讓您撰寫任何平台均適用的程式碼，以瀏覽檔案系統。 因為它是跨平臺的,它包含與 Windows 系統無關的 API。 例如,`is_fifo(const path&)`始終在 Windows 上傳回**false。**

## <a name="overview"></a>概觀

使用 \<filesystem> API 進行下列工作：

- 反覆查看指定路徑下的檔案和目錄

- 取得檔案的相關資訊，包括建立時間、大小、副檔名和根目錄

- 撰寫、分解以及比較路徑

- 建立、複製與移除目錄

- 複製和刪除檔案

如需使用標準程式庫之檔案 IO 的詳細資訊，請參閱 [iostream 程式設計](../standard-library/iostream-programming.md)。

## <a name="paths"></a>路徑

### <a name="constructing-and-composing-paths"></a>建構和組成路徑

Windows (自從 XP 以來) 中的路徑會以 Unicode 原生儲存。 [路徑](../standard-library/path-class.md)類會自動執行所有必要的字串轉換。 它接受寬字元陣列和窄字元陣列的參數,`std::string``std::wstring`以及格式化為 UTF8 或 UTF16 的類型。 `path` 類別也會自動正規化路徑分隔符號。 您可以使用單一正斜線做為建構函式引數中的目錄分隔符號。 此分隔符允許您使用相同的字串在 Windows 和 UNIX 環境中儲存路徑:

```cpp
path pathToDisplay(L"/FileSystemTest/SubDir3");     // OK!
path pathToDisplay2(L"\\FileSystemTest\\SubDir3");  // Still OK as always
path pathToDisplay3(LR"(\FileSystemTest\SubDir3)"); // Raw string literals are OK, too.
```

若要串連兩個路徑，可以使用多載的 `/` 及 `/=` 運算子。這兩個運算子類似於 `std::string` 及 `std::wstring` 上的 `+` 和 `+=` 運算子。 如果沒有`path`,物件將方便地提供分隔符。

```cpp
path myRoot("C:/FileSystemTest");  // no trailing separator, no problem!
myRoot /= path("SubDirRoot");      // C:/FileSystemTest/SubDirRoot
```

### <a name="examining-paths"></a>檢查路徑

路徑類具有多種方法來返回有關路徑本身各個部分的資訊。 此資訊與它可能引用的檔案系統實體的資訊不同。 您可以取得根、相對路徑、檔名、副檔名等等。 您可以反覆查看路徑物件，檢查階層中的所有資料夾。 下面的範例演示如何在路徑物件上反覆運算。 以及如何檢索有關其部件的資訊。

```cpp
// filesystem_path_example.cpp
// compile by using: /EHsc /W4 /permissive- /std:c++17 (or /std:c++latest)
#include <string>
#include <iostream>
#include <sstream>
#include <filesystem>

using namespace std;
using namespace std::filesystem;

wstring DisplayPathInfo()
{
    // This path may or may not refer to an existing file. We are
    // examining this path string, not file system objects.
    path pathToDisplay(L"C:/FileSystemTest/SubDir3/SubDirLevel2/File2.txt ");

    wostringstream wos;
    int i = 0;
    wos << L"Displaying path info for: " << pathToDisplay << endl;
    for (path::iterator itr = pathToDisplay.begin(); itr != pathToDisplay.end(); ++itr)
    {
        wos << L"path part: " << i++ << L" = " << *itr << endl;
    }

    wos << L"root_name() = " << pathToDisplay.root_name() << endl
        << L"root_path() = " << pathToDisplay.root_path() << endl
        << L"relative_path() = " << pathToDisplay.relative_path() << endl
        << L"parent_path() = " << pathToDisplay.parent_path() << endl
        << L"filename() = " << pathToDisplay.filename() << endl
        << L"stem() = " << pathToDisplay.stem() << endl
        << L"extension() = " << pathToDisplay.extension() << endl;

    return wos.str();
}

int main()
{
    wcout << DisplayPathInfo() << endl;
    // wcout << ComparePaths() << endl; // see following example
    wcout << endl << L"Press Enter to exit" << endl;
    wstring input;
    getline(wcin, input);
}
```

程式碼會產生以下輸出：

```Output
Displaying path info for: C:\FileSystemTest\SubDir3\SubDirLevel2\File2.txt
path part: 0 = C:
path part: 1 = \
path part: 2 = FileSystemTest
path part: 3 = SubDir3
path part: 4 = SubDirLevel2
path part: 5 = File2.txt
root_name() = C:
root_path() = C:\
relative_path() = FileSystemTest\SubDir3\SubDirLevel2\File2.txt
parent_path() = C:\FileSystemTest\SubDir3\SubDirLevel2
filename() = File2.txt
stem() = File2
extension() = .txt
```

### <a name="comparing-paths"></a>比較路徑

`path` 類別會多載與 `std::string` 及 `std::wstring`相同的比較運算子。 比較兩條路徑時,在分隔符規範化後進行字串比較。 如果缺少尾隨斜杠(或反斜杠),則不會添加它,這會影響比較。 下列範例將示範如何比較路徑值：

```cpp
wstring ComparePaths()
{
    path p0(L"C:/Documents");                 // no trailing separator
    path p1(L"C:/Documents/");                // p0 < p1
    path p2(L"C:/Documents/2013/");           // p1 < p2
    path p3(L"C:/Documents/2013/Reports/");   // p2 < p3
    path p4(L"C:/Documents/2014/");           // p3 < p4
    path p5(L"D:/Documents/2013/Reports/");   // p4 < p5

    wostringstream wos;
    wos << boolalpha <<
        p0.wstring() << L" < " << p1.wstring() << L": " << (p0 < p1) << endl <<
        p1.wstring() << L" < " << p2.wstring() << L": " << (p1 < p2) << endl <<
        p2.wstring() << L" < " << p3.wstring() << L": " << (p2 < p3) << endl <<
        p3.wstring() << L" < " << p4.wstring() << L": " << (p3 < p4) << endl <<
        p4.wstring() << L" < " << p5.wstring() << L": " << (p4 < p5) << endl;
    return wos.str();
}
```

```Output
C:\Documents < C:\Documents\: true
C:\Documents\ < C:\Documents\2013\: true
C:\Documents\2013\ < C:\Documents\2013\Reports\: true
C:\Documents\2013\Reports\ < C:\Documents\2014\: true
C:\Documents\2014\ < D:\Documents\2013\Reports\: true
```

若要執行此程式碼，請將其貼到完整範例上方的 `main` 之前，並取消註解 main 中呼叫程式碼的那一行。

### <a name="converting-between-path-and-string-types"></a>在路徑和字串類型之間轉換

`path` 物件隱含可以轉換成 `std::wstring` 或 `std::string`的能力。 這意味著您可以將路徑傳遞給函數,如[wofstream::open,](../standard-library/basic-ofstream-class.md#open)如本示例所示:

```cpp
// filesystem_path_conversion.cpp
// compile by using: /EHsc /W4 /permissive- /std:c++17 (or /std:c++latest)
#include <string>
#include <iostream>
#include <fstream>
#include <filesystem>

using namespace std;
using namespace std::filesystem;

int main()
{
    const wchar_t* p{ L"C:/Users/Public/Documents" };
    path filePath(p);

    filePath /= L"NewFile.txt";

    // Open, write to, and close the file.
    wofstream writeFile(filePath, ios::out);  // implicit conversion
    writeFile << L"Lorem ipsum\nDolor sit amet";
    writeFile.close();

    // Open, read, and close the file.
    wifstream readFile;
    wstring line;
    readFile.open(filePath);  // implicit conversions
    wcout << L"File " << filePath << L" contains:" << endl;
    while (readFile.good())
    {
        getline(readFile, line);
        wcout << line << endl;
    }
    readFile.close();

    wcout << endl << L"Press Enter to exit" << endl;
    wstring input;
    getline(wcin, input);
}
```

```Output
File C:\Users\Public\Documents\NewFile.txt contains:
Lorem ipsum
Dolor sit amet

Press Enter to exit
```

## <a name="iterating-directories-and-files"></a>逐一查看目錄和檔案

\<filesystem> 標頭提供 [directory_iterator](../standard-library/directory-iterator-class.md) 類型，可反覆查看單一目錄，並提供 [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) 類別，以遞迴方式反覆查看目錄及其子目錄。 當您藉由傳遞 `path` 來建構迭代器之後，迭代器會指向路徑中的第一個 directory_entry。 透過呼叫預設建構函式來建立結尾迭代器。

在瀏覽目錄時,您可能會發現多種類型的專案。 這些專案包括目錄、檔、符號連結、套接字檔等。 `directory_iterator` 會以 [directory_entry](../standard-library/directory-entry-class.md) 物件形式傳回它的項目。
