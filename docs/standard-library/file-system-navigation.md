---
title: "檔案系統巡覽 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: f7cc5f5e-a541-4e00-87c7-a3769ef6096d
caps.latest.revision: 14
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 檔案系統巡覽
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<Filesystem\> 標頭會實作檔案系統技術規格草案 \([ISO\/IEC JTC SC 1\/22\/WG 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf)\)，並會提供可以讓您撰寫任何平台均適用之程式碼的類型與函式，以瀏覽檔案系統。 由於是跨平台標頭，其包含與 Windows 系統不相關的 API。 例如，這表示 `is_fifo(const path&)` 在 Windows 上一律會傳回 `false`。 截至 Visual Studio 2015 RTM 為止，此標頭所使用的技術規格草案，並未獲選為 C\+\+17 標準。 您可以在 `std::experimental::filesystem::v1` 命名空間中找到其成員。  
  
## 概觀  
 使用 \<filesystem\> API 進行下列工作：  
  
-   反覆查看指定路徑下的檔案和目錄  
  
-   取得檔案的相關資訊，包括建立時間、大小、副檔名和根目錄  
  
-   撰寫、分解以及比較路徑  
  
-   建立、複製以及刪除目錄  
  
-   複製和刪除檔案  
  
 如需使用標準程式庫之檔案 IO 的詳細資訊，請參閱 [iostream 程式設計](../standard-library/iostream-programming.md)。  
  
## 路徑  
  
### 建構和組成路徑  
 Windows \(自從 XP 以來\) 中的路徑會以 Unicode 原生儲存。[path](../standard-library/path-class-cpp-standard-template-library.md) 類別會自動執行所有必要的字串轉換。 除了接受寬字元陣列與窄字元陣列，也接受 UTF8 或 UTF16 格式的 `std::string` 及 `std::wstring` 類型。`path` 類別也會自動正規化路徑分隔符號。 您可以使用單一正斜線做為建構函式引數中的目錄分隔符號。 這可讓您使用相同的字串儲存 Windows 和 UNIX 環境中的路徑：  
  
```cpp  
path pathToDisplay(L"/FileSystemTest/SubDir3"); // OK! path pathToDisplay2(L"\\FileSystemTest\\SubDir3"); // Still OK as always path pathToDisplay3(LR"(\FileSystemTest\SubDir3)"); // Raw string literals are OK, too.  
```  
  
 若要串連兩個路徑，可以使用多載的  `/` 及 `/=` 運算子。這兩個運算子類似於 `std::string` 及 `std::wstring` 上的 `+``+=` 運算子。 若您未提供分隔符號，`path` 物件將會適時提供。  
  
```cpp  
path myRoot("C:/FileSystemTest"); // no trailing separator, no problem! myRoot /= path("SubDirRoot"); // C:/FileSystemTest/SubDirRoot  
```  
  
### 檢查路徑  
 Path 類別有數個方法可傳回路徑本身各個部分的相關資訊，且不同於它所指的檔案系統實體。 您可以取得根、相對路徑、檔名、副檔名等等。 您可以反覆查看路徑物件，檢查階層中的所有資料夾。 下列範例將顯示如何反覆查看路徑 \(而非它所指的目錄\)，以及擷取其各部分的相關資訊。  
  
```cpp  
  
#include <string> #include <iostream> #include <sstream> #include <filesystem> using namespace std; using namespace std::experimental::filesystem::v1; wstring  DisplayPathInfo() { // This path may or may not refer to an existing file. We are // examining this path string, not file system objects. path pathToDisplay(L"C:/FileSystemTest/SubDir3/SubDirLevel2/File2.txt "); wostringstream wos; int i = 0; wos << L"Displaying path info for: " << pathToDisplay << endl; for (path::iterator itr = pathToDisplay.begin(); itr != pathToDisplay.end(); ++itr) { wos << L"path part: " << i++ << L" = " << *itr << endl; } wos << L"root_name() = " << pathToDisplay.root_name() << endl << L"root_path() = " << pathToDisplay.root_path() << endl << L"relative_path() = " << pathToDisplay.relative_path() << endl << L"parent_path() = " << pathToDisplay.parent_path() << endl << L"filename() = " << pathToDisplay.filename() << endl << L"stem() = " << pathToDisplay.stem() << endl << L"extension() = " << pathToDisplay.extension() << endl; return wos.str(); } void main(int argc, char* argv[]) { wcout << DisplayPathInfo() << endl; // wcout << ComparePaths() << endl; // see following example wcout << endl << L"Press Enter to exit" << endl; wstring input; getline(wcin, input); }  
```  
  
 程式碼會產生以下輸出：  
  
```cpp  
Displaying path info for: C:\FileSystemTest\SubDir3\SubDirLevel2\File2.txt path part: 0 = C: path part: 1 = \ path part: 2 = FileSystemTest path part: 3 = SubDir3 path part: 4 = SubDirLevel2 path part: 5 = File2.txt root_name() = C: root_path() = C:\ relative_path() = FileSystemTest\SubDir3\SubDirLevel2\File2.txt parent_path() = C:\FileSystemTest\SubDir3\SubDirLevel2 filename() = File2.txt stem() = File2 extension() = .txt  
```  
  
### 比較路徑  
 `path` 類別會多載與 `std::string` 及 `std::wstring` 相同的比較運算子。 當比較兩個路徑時，您是在正規化分隔符號之後執行字串比較。 如果找不到結尾的斜線 \(或反斜線\)，即代表沒有將其加入，並會影響比較。 下列範例將示範如何比較路徑值：  
  
```cpp  
  
wstring ComparePaths() { path p0(L"C:/Documents"); // no trailing separator path p1(L"C:/Documents/"); //p0 < p1 path p2(L"C:/Documents/2013/"); // p1 < p2 path p3(L"C:/Documents/2013/Reports/"); // p2 < p3 path p4(L"C:/Documents/2014/");  // p3 < p4 path p5(L"D:/Documents/2013/Reports/"); // p4 < p5 wostringstream wos; wos << boolalpha << p0.wstring() << L" < " << p1.wstring() << L": " << (p0 < p1) << endl << p1.wstring() << L" < " << p2.wstring() << L": " << (p1 < p2) << endl << p2.wstring() << L" < " << p3.wstring() << L": " << (p2 < p3) << endl << p3.wstring() << L" < " << p4.wstring() << L": " << (p3 < p4) << endl << p4.wstring() << L" < " << p5.wstring() << L": " << (p4 < p5) << endl; return wos.str(); } /* Output: C:\Documents < C:\Documents\: true C:\Documents\ < C:\Documents\2013\: true C:\Documents\2013\ < C:\Documents\2013\Reports\: true C:\Documents\2013\Reports\ < C:\Documents\2014\: true C:\Documents\2014\ < D:\Documents\2013\Reports\: true */  
```  
  
 若要執行此程式碼，請將其貼到完整範例的上方，並取消註解 main 中呼叫它的該行。  
  
### 在路徑和字串類型之間轉換  
 `path` 物件隱含可以轉換成 `std::wstring` 或 `std::string` 的能力。 這表示您可以將路徑傳遞至例如 [wofstream::open](../Topic/basic_ofstream::open.md) 的函式，如此範例中所示：  
  
```cpp  
wchar_t* p = L"C:/test"; path filePath(p); filePath /= L"NewFile.txt"; // Open, write to, and close the file. wofstream myFile; myFile.open(filePath); myFile << L"Lorem ipsum..."; myFile.close  
  
```  
  
## 逐一查看目錄和檔案  
 \<filesystem\> 標頭提供 [directory\_iterator](../standard-library/directory-iterator-class.md) 類型，可反覆查看單一目錄，並提供 [recursive\_directory\_iterator](../standard-library/recursive-directory-iterator-class.md) 類別，以遞迴方式反覆查看目錄及其子目錄。 當您藉由傳遞 `path` 來建構迭代器之後，迭代器會指向路徑中的第一個 directory\_entry。 透過呼叫預設建構函式來建立結尾迭代器。  
  
 當逐一查看目錄時，您可能會遇到幾種項目，包括但不限於目錄、檔案、符號連結和通訊端檔案。`directory_iterator` 會以 [directory\_entry](../standard-library/directory-entry-class.md) 物件形式傳回其項目，而且每個物件皆具有 [status\(\)](http://msdn.microsoft.com/zh-tw/a70a3c55-3a76-417f-abaf-862ff94b2056) 成員，告訴您正在查看的項目類型。 藉由檢查此值，您可以決定要對任何特定項目執行的工作。 下列範例會反覆查看單一目錄，如果目錄項目是一般檔案，則程式碼會列印出該檔案的一些資訊。 如果項目是目錄，則只會顯示名稱。  
  
```cpp  
#include <string> #include <iostream> #include <iomanip> #include <filesystem> #include <chrono> #include <time.h> using namespace std; using namespace std::experimental::filesystem::v1; // Display the last write time for the file wstring LastWriteTimeToLocalTime(const path& file_path) { const auto last = chrono::system_clock::to_time_t(last_write_time(file_path)); tm timeinfo; localtime_s(&timeinfo, &last); wchar_t buf[56]; _wasctime_s(buf, 56, &timeinfo); // appends '\n' return wstring{ buf }; } // List files and directories in the specified path void DisplayFolderContents(const path& p) { wcout << L"Begin iterating " << p.wstring() << endl; for (const auto& entry : directory_iterator{ p }) { if (is_regular_file(entry.status())) { wcout << L" File: " << entry.path().filename() << " : " << LastWriteTimeToLocalTime(entry.path()); } else if (is_directory(entry.status())) { wcout << L" Dir: " << entry.path().filename() << endl; } } } void main() { wstring dir{ LR"(C:\users\public\documents\)" }; path p{ dir }; if (!is_directory(p)) { wcout << L"No such directory: " << dir << endl; return; } DisplayFolderContents(p); // IterateFolderRecursively(p); // see example wcout << endl << L"Press Enter to exit" << endl; wstring input; getline(wcin, input); }  
```  
  
### 以遞迴方式逐一查看目錄樹狀結構  
 下列範例將示範如何以遞迴方式逐一查看目錄樹狀結構。 若要執行此函式，請將其貼到先前的程式碼範例中的 DisplayFolderContents 函式之後，並取消註解 main 中呼叫它的該行。  
  
```cpp  
// List files and directories recursively in the path void IterateFolderRecursively(const path& p) { wcout << L"Begin iterating " << p.wstring() << " recursively" << endl; for (recursive_directory_iterator it{ p }, end; it != end; ++it) { if (is_regular_file(it->status())) { wcout << setw(it.depth()) << L" " << L"File: " << it->path().filename() << L" : " << LastWriteTimeToLocalTime(it->path()); } else if (is_directory(it->status())) { wcout << setw(it.depth()) << L" " << L"Dir: " << it->path().filename() << endl; } } }  
```  
  
### 處理符號連結  
 到 Visual Studio 2015 為止，在 Visual C\+\+ 尚不支援符號連結偵測。