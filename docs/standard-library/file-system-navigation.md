---
title: 檔案系統巡覽
description: 如何使用 c + + 標準程式庫 filesystem Api 來流覽檔案系統。
ms.date: 04/13/2020
ms.assetid: f7cc5f5e-a541-4e00-87c7-a3769ef6096d
ms.openlocfilehash: 26abe2fad6cacf8959507f15e967278e85254024
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203282"
---
# <a name="file-system-navigation"></a>檔案系統巡覽

此 \<filesystem> 標頭會執行 c + + 檔案系統技術規格 ISO/IEC TS 18822:2015 （最終草稿： [ISO/iec JTC 1/SC 22/WG 21 N4100](https://wg21.link/n4100)），而且具有類型和函式，可讓您撰寫與平臺無關的程式碼來流覽檔案系統。 因為它是跨平臺的，所以包含與 Windows 系統無關的 Api。 例如， `is_fifo(const path&)` **`false`** 在 Windows 上一律會傳回。

## <a name="overview"></a>概觀

使用 \<filesystem> api 來執行下列工作：

- 反覆查看指定路徑下的檔案和目錄

- 取得檔案的相關資訊，包括建立時間、大小、副檔名和根目錄

- 撰寫、分解以及比較路徑

- 建立、複製和刪除目錄

- 複製和刪除檔案

如需使用標準程式庫之檔案 IO 的詳細資訊，請參閱 [iostream 程式設計](../standard-library/iostream-programming.md)。

## <a name="paths"></a>路徑

### <a name="constructing-and-composing-paths"></a>建構和組成路徑

Windows (自從 XP 以來) 中的路徑會以 Unicode 原生儲存。 [Path](../standard-library/path-class.md)類別會自動執行所有必要的字串轉換。 它接受寬和窄字元陣列的引數，以及 `std::string` `std::wstring` 格式為 UTF8 或 UTF16 的和類型。 `path` 類別也會自動正規化路徑分隔符號。 您可以使用單一正斜線做為建構函式引數中的目錄分隔符號。 這個分隔符號可讓您使用相同的字串，在 Windows 和 UNIX 環境中儲存路徑：

```cpp
path pathToDisplay(L"/FileSystemTest/SubDir3");     // OK!
path pathToDisplay2(L"\\FileSystemTest\\SubDir3");  // Still OK as always
path pathToDisplay3(LR"(\FileSystemTest\SubDir3)"); // Raw string literals are OK, too.
```

若要串連兩個路徑，可以使用多載的 `/` 及 `/=` 運算子。這兩個運算子類似於 `std::string` 及 `std::wstring` 上的 `+` 和 `+=` 運算子。 `path`如果您沒有的話，物件會方便提供分隔符號。

```cpp
path myRoot("C:/FileSystemTest");  // no trailing separator, no problem!
myRoot /= path("SubDirRoot");      // C:/FileSystemTest/SubDirRoot
```

### <a name="examining-paths"></a>檢查路徑

Path 類別有數個方法，會傳回路徑本身的各個部分的相關資訊。 這種資訊與它可能參考的檔案系統實體相關的資訊不同。 您可以取得根、相對路徑、檔名、副檔名等等。 您可以反覆查看路徑物件，檢查階層中的所有資料夾。 下列範例顯示如何逐一查看 path 物件。 以及如何取得其元件的相關資訊。

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

`path` 類別會多載與 `std::string` 及 `std::wstring`相同的比較運算子。 當您比較兩個路徑時，您可以在將分隔符號正規化之後進行字串比較。 如果遺漏尾端斜線（或反斜線），則不會加入它，而且會影響比較。 下列範例將示範如何比較路徑值：

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

`path` 物件隱含可以轉換成 `std::wstring` 或 `std::string`的能力。 這表示您可以將路徑傳遞至函式，例如[wofstream：： open](../standard-library/basic-ofstream-class.md#open)，如下列範例所示：

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

\<filesystem>標頭會提供[directory_iterator](../standard-library/directory-iterator-class.md)類型來反復查看單一目錄，而[recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md)類別則會在目錄及其子目錄上逐一查看。 當您藉由傳遞 `path` 來建構迭代器之後，迭代器會指向路徑中的第一個 directory_entry。 透過呼叫預設建構函式來建立結尾迭代器。

逐一查看目錄時，您可能會發現幾種類型的專案。 這些專案包括目錄、檔案、符號連結、通訊端檔案等等。 `directory_iterator` 會以 [directory_entry](../standard-library/directory-entry-class.md) 物件形式傳回它的項目。
