---
title: HOW TO：例外狀況和非例外狀況代碼之間的介面
ms.custom: how-to
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fd5bb4af-5665-46a1-a321-614b48d4061e
ms.openlocfilehash: e8ff92f965f48faa7954ae0364ec7877428e519c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183696"
---
# <a name="how-to-interface-between-exceptional-and-non-exceptional-code"></a>HOW TO：例外狀況和非例外狀況代碼之間的介面

本文說明如何在 C++ 模組實作一致的例外狀況處理，以及如何將這些例外狀況與在例外狀況界限上的錯誤碼來回轉譯。

有時候 C++ 模組必須與不使用例外狀況的程式碼 (非例外狀況程式碼) 接合。 這種介面稱為*例外狀況界限*。 例如，可以在 C++ 程式中呼叫 Win32 函式 `CreateFile`。 `CreateFile` 不會擲回例外狀況，而是設定可由 `GetLastError` 函式擷取的錯誤碼。 如果您的 C++ 程式為非一般的，您可能想要有一致的例外狀況架構錯誤處理原則。 而且您可能不想要因為您正在使用非例外狀況程式碼而放棄例外狀況，也不想要在 C++ 模組中混合例外狀況架構和非例外狀況架構的錯誤處理原則。

## <a name="calling-non-exceptional-functions-from-c"></a>從 C++ 呼叫非例外狀況函式

當您從 C++ 呼叫非例外狀況函式，這個概念是將函式包裝在可偵測所有錯誤然後擲回例外狀況的 C++ 函式中。 當您設計這類包裝函式時，先決定要提供哪種例外狀況保證：不擲回、強式或基本。 其次，設計函式，以致擲回例外狀況時正確地釋放所有資源，例如，檔案控制代碼。 通常，這表示您使用智慧型指標或類似的資源管理員擁有資源。 如需有關設計考量的詳細資訊，請參閱[How to:例外狀況安全的設計](../cpp/how-to-design-for-exception-safety.md)。

### <a name="example"></a>範例

下列範例顯示 C++ 函式內部使用 Win32 `CreateFile` 和 `ReadFile` 函式開啟和讀取兩個檔案。  `File` 類別是檔案控制代碼的「資源擷取為初始設定」(Resource Acquisition Is Initialization，RAII) 包裝函式。 其建構函式偵測「找不到檔案」條件並擲回例外狀況，以將錯誤傳播至 C++ 模組的呼叫堆疊 (在此範例中為 `main()` 函式)。 如果於 `File` 物件完全建構之後擲回例外狀況，解構函式會被自動呼叫 `CloseHandle` 以釋放檔案控制代碼  (如果您想要的話，您可以為這個相同的目的使用 Active Template Library (ATL) `CHandle` 類別或與自訂刪除者一起使用 `unique_ptr`)。呼叫 Win32 和 CRT API 的函式偵測錯誤然後使用本機定義的 `ThrowLastErrorIf` 函式擲回 C++ 例外狀況，而後者則會使用衍生自 `Win32Exception` 類別的 `runtime_error` 類別。 這個範例中的所有函式提供強式例外狀況保證；如果例外狀況在這些函式的任何時候擲回，資源不會流失，也不會修改程式狀態。

```cpp
// compile with: /EHsc
#include <Windows.h>
#include <stdlib.h>
#include <vector>
#include <iostream>
#include <string>
#include <limits>
#include <stdexcept>

using namespace std;

string FormatErrorMessage(DWORD error, const string& msg)
{
    static const int BUFFERLENGTH = 1024;
    vector<char> buf(BUFFERLENGTH);
    FormatMessageA(FORMAT_MESSAGE_FROM_SYSTEM, 0, error, 0, buf.data(),
        BUFFERLENGTH - 1, 0);
    return string(buf.data()) + "   ("  + msg  + ")";
}

class Win32Exception : public runtime_error
{
private:
    DWORD m_error;
public:
    Win32Exception(DWORD error, const string& msg)
        : runtime_error(FormatErrorMessage(error, msg)), m_error(error) { }

    DWORD GetErrorCode() const { return m_error; }
};

void ThrowLastErrorIf(bool expression, const string& msg)
{
    if (expression) {
        throw Win32Exception(GetLastError(), msg);
    }
}

class File
{
private:
    HANDLE m_handle;

    // Declared but not defined, to avoid double closing.
    File& operator=(const File&);
    File(const File&);
public:
    explicit File(const string& filename)
    {
        m_handle = CreateFileA(filename.c_str(), GENERIC_READ, FILE_SHARE_READ,
            nullptr, OPEN_EXISTING, FILE_ATTRIBUTE_READONLY, nullptr);
        ThrowLastErrorIf(m_handle == INVALID_HANDLE_VALUE,
            "CreateFile call failed on file named " + filename);
    }

    ~File() { CloseHandle(m_handle); }

    HANDLE GetHandle() { return m_handle; }
};

size_t GetFileSizeSafe(const string& filename)
{
    File fobj(filename);
    LARGE_INTEGER filesize;

    BOOL result = GetFileSizeEx(fobj.GetHandle(), &filesize);
    ThrowLastErrorIf(result == FALSE, "GetFileSizeEx failed: " + filename);

    if (filesize.QuadPart < (numeric_limits<size_t>::max)()) {
        return filesize.QuadPart;
    } else {
        throw;
    }
}

vector<char> ReadFileVector(const string& filename)
{
    File fobj(filename);
    size_t filesize = GetFileSizeSafe(filename);
    DWORD bytesRead = 0;

    vector<char> readbuffer(filesize);

    BOOL result = ReadFile(fobj.GetHandle(), readbuffer.data(), readbuffer.size(),
        &bytesRead, nullptr);
    ThrowLastErrorIf(result == FALSE, "ReadFile failed: " + filename);

    cout << filename << " file size: " << filesize << ", bytesRead: "
        << bytesRead << endl;

    return readbuffer;
}

bool IsFileDiff(const string& filename1, const string& filename2)
{
    return ReadFileVector(filename1) != ReadFileVector(filename2);
}

#include <iomanip>

int main ( int argc, char* argv[] )
{
    string filename1("file1.txt");
    string filename2("file2.txt");

    try
    {
        if(argc > 2) {
            filename1 = argv[1];
            filename2 = argv[2];
        }

        cout << "Using file names " << filename1 << " and " << filename2 << endl;

        if (IsFileDiff(filename1, filename2)) {
            cout << "+++ Files are different." << endl;
        } else {
            cout<< "=== Files match." << endl;
        }
    }
    catch(const Win32Exception& e)
    {
        ios state(nullptr);
        state.copyfmt(cout);
        cout << e.what() << endl;
        cout << "Error code: 0x" << hex << uppercase << setw(8) << setfill('0')
            << e.GetErrorCode() << endl;
        cout.copyfmt(state); // restore previous formatting
    }
}
```

## <a name="calling-exceptional-code-from-non-exceptional-code"></a>從非例外狀況程式碼呼叫例外狀況程式碼

宣告為「extern C」的 C++ 函式可以由 C 程式呼叫。 C++ COM 伺服器可由以一些不同的語言撰寫的程式碼使用。 當您實作由非例外狀況程式碼呼叫的 C++ 公用例外狀況感知函式，C++ 函式不應該允許任何例外狀況傳播回呼叫端。 因此，C++ 函式必須明確攔截它知道如何處理的例外狀況，如果可行，將例外狀況轉換成錯誤碼以讓呼叫端了解例外狀況。 如果不是所有可能的例外狀況都是已知，C++ 函式應該具有 `catch(...)` 區塊做為最後一個處理常式。 在這種情況下，因為您的程式可能處於未知的狀態，最好向呼叫端報告嚴重錯誤。

下列範例會示範函式假設可能擲回的任何例外狀況是 Win32Exception 或衍生自 `std::exception` 的例外狀況類型。 函式攔截這些類型的任何例外狀況，並將錯誤資訊做為 Win32 錯誤碼傳遞給呼叫端。

```cpp
BOOL DiffFiles2(const string& file1, const string& file2)
{
    try
    {
        File f1(file1);
        File f2(file2);
        if (IsTextFileDiff(f1, f2))
        {
            SetLastError(MY_APPLICATION_ERROR_FILE_MISMATCH);
            return FALSE;
        }
        return TRUE;
    }
    catch(Win32Exception& e)
    {
        SetLastError(e.GetErrorCode());
    }

    catch(std::exception& e)
    {
        SetLastError(MY_APPLICATION_GENERAL_ERROR);
    }
    return FALSE;
}
```

當您將例外狀況轉換為錯誤碼時，一個可能發生的問題是錯誤碼通常不包含例外狀況可以儲存的豐富資訊。 若要解決此問題，您可以提供**攔截**區塊的每個特定的例外狀況類型可能會擲回，並執行它轉換為錯誤碼之前記錄例外狀況的詳細資料。 這種方法可以建立許多重複的程式碼，如果多個函式都會使用相同的一組**攔截**區塊。 若要避免重複的程式碼的好方法是重構這些區塊至一個私用公用程式函式實作**嘗試**並**攔截**區塊，以及接受中會叫用的函式物件**嘗試**區塊。 在每個公用函式，將程式碼做為 Lambda 運算式傳遞至這個公用程式函式。

```cpp
template<typename Func>
bool Win32ExceptionBoundary(Func&& f)
{
    try
    {
        return f();
    }
    catch(Win32Exception& e)
    {
        SetLastError(e.GetErrorCode());
    }
    catch(const std::exception& e)
    {
        SetLastError(MY_APPLICATION_GENERAL_ERROR);
    }
    return false;
}
```

下列範例顯示如何撰寫定義仿函式的 Lambda 運算式。 當仿函式用 Lambda 運算式「內嵌」定義時，通常比寫入為具名函式物件更為容易讀取。

```cpp
bool DiffFiles3(const string& file1, const string& file2)
{
    return Win32ExceptionBoundary([&]() -> bool
    {
        File f1(file1);
        File f2(file2);
        if (IsTextFileDiff(f1, f2))
        {
            SetLastError(MY_APPLICATION_ERROR_FILE_MISMATCH);
            return false;
        }
        return true;
    });
}
```

如需 Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../cpp/lambda-expressions-in-cpp.md)。

## <a name="see-also"></a>另請參閱

[錯誤和例外狀況處理 (現代 C++)](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[如何：例外狀況安全的設計](../cpp/how-to-design-for-exception-safety.md)<br/>
