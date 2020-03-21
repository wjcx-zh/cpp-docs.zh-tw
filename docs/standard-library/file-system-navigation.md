---
title: 檔案系統巡覽
ms.date: 11/04/2016
ms.assetid: f7cc5f5e-a541-4e00-87c7-a3769ef6096d
ms.openlocfilehash: f5fe8d29baae76b1e7fb851bf04f4c6b32215a8e
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076534"
---
# <a name="file-system-navigation"></a>檔案系統巡覽

\<filesystem> 標頭會實作 C++ 檔案系統技術規格 ISO/IEC TS 18822:2015 (草案最終版：[ISO/IEC JTC 1/SC 22/WG 21 N4100](https://wg21.link/n4100))，並提供相關類型與函式，讓您撰寫任何平台均適用的程式碼，以瀏覽檔案系統。 由於是跨平台標頭，其包含與 Windows 系統不相關的 API。 例如，這表示 `is_fifo(const path&)` 一律會在 Windows 上傳回**false** 。

## <a name="overview"></a>概觀

使用 \<filesystem> API 進行下列工作：

- 反覆查看指定路徑下的檔案和目錄

- 取得檔案的相關資訊，包括建立時間、大小、副檔名和根目錄

- 撰寫、分解以及比較路徑

- 建立、複製以及刪除目錄

- 複製和刪除檔案

如需使用標準程式庫之檔案 IO 的詳細資訊，請參閱 [iostream 程式設計](../standard-library/iostream-programming.md)。

## <a name="paths"></a>路徑

### <a name="constructing-and-composing-paths"></a>建構和組成路徑

Windows (自從 XP 以來) 中的路徑會以 Unicode 原生儲存。 [path](../standard-library/path-class.md) 類別會自動執行所有必要的字串轉換。 除了接受寬字元陣列與窄字元陣列，也接受 UTF8 或 UTF16 格式的 `std::string` 及 `std::wstring` 類型。 `path` 類別也會自動正規化路徑分隔符號。 您可以使用單一正斜線做為建構函式引數中的目錄分隔符號。 這可讓您使用相同的字串儲存 Windows 和 UNIX 環境中的路徑：

```cpp
path pathToDisplay(L"/FileSystemTest/SubDir3");     // OK!
path pathToDisplay2(L"\\FileSystemTest\\SubDir3");  // Still OK as always
path pathToDisplay3(LR"(\FileSystemTest\SubDir3)"); // Raw string literals are OK, too.
```

若要串連兩個路徑，可以使用多載的 `/` 及 `/=` 運算子。這兩個運算子類似於 `+` 及 `+=` 上的 `std::string` 和 `std::wstring` 運算子。 如果您沒有的話，`path` 物件可以方便地提供分隔符號。

```cpp
path myRoot("C:/FileSystemTest");  // no trailing separator, no problem!
myRoot /= path("SubDirRoot");      // C:/FileSystemTest/SubDirRoot
```

### <a name="examining-paths"></a>檢查路徑

Path 類別有數個方法可傳回路徑本身各個部分的相關資訊，且不同於它所指的檔案系統實體。 您可以取得根、相對路徑、檔名、副檔名等等。 您可以反覆查看路徑物件，檢查階層中的所有資料夾。 下列範例將顯示如何反覆查看路徑 (而非它所指的目錄)，以及擷取其各部分的相關資訊。

```cpp
// filesystem_path_example.cpp
// compile by using: /EHsc
#include <string>
#include <iostream>
#include <sstream>
#include <filesystem>

using namespace std;
using namespace std::experimental::filesystem;

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

int main(int argc, char* argv[])
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

`path` 類別會多載與 `std::string` 及 `std::wstring`相同的比較運算子。 當比較兩個路徑時，您是在正規化分隔符號之後執行字串比較。 如果找不到結尾的斜線 (或反斜線)，即代表沒有將其加入，並會影響比較。 下列範例將示範如何比較路徑值：

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

`path` 物件隱含可以轉換成 `std::wstring` 或 `std::string`的能力。 這表示您可以將路徑傳遞至 [wofstream::open](../standard-library/basic-ofstream-class.md#open) 這類函式，如此範例中所示：

```cpp
// filesystem_path_conversion.cpp
// compile by using: /EHsc
#include <string>
#include <iostream>
#include <fstream>
#include <filesystem>

using namespace std;
using namespace std::experimental::filesystem;

int main(int argc, char* argv[])
{
    wchar_t* p = L"C:/Users/Public/Documents";
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

當逐一查看目錄時，您可能會遇到幾種項目，包括但不限於目錄、檔案、符號連結和通訊端檔案。 `directory_iterator` 會以 [directory_entry](../standard-library/directory-entry-class.md) 物件形式傳回它的項目。
