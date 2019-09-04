---
title: '#using 指示詞C++(/cli)'
ms.date: 08/29/2019
f1_keywords:
- friend_as_cpp
- '#using'
- friend_as
- '#using_cpp'
helpviewer_keywords:
- using directive (#using)
- '#using directive'
- LIBPATH environment variable
- preprocessor, directives
ms.assetid: 870b15e5-f361-40a8-ba1c-c57d75c8809a
ms.openlocfilehash: 5dae5c277055157aef5451c19ee020fbbd2aaccb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220206"
---
# <a name="using-directive-ccli"></a>#using 指示詞C++(/cli)

將中繼資料匯入使用[/clr](../build/reference/clr-common-language-runtime-compilation.md)編譯的程式。

## <a name="syntax"></a>語法

> **#using**檔案[**as_friend**]

### <a name="parameters"></a>參數

*文字檔*\
MSIL .dll、.exe、.netmodule 或 .obj。例如，套用至物件的

`#using <MyComponent.dll>`

**as_friend**\
指定檔案中的所有類型都可以存取。 如需詳細資訊, 請參閱[FriendC++元件 ()](../dotnet/friend-assemblies-cpp.md)。

## <a name="remarks"></a>備註

檔案可以是 Microsoft 中繼語言 (MSIL) 檔案, 您可以為其管理的資料和受控結構匯入該檔案。 如果 .dll 檔案包含組件資訊清單, 則會匯入資訊清單中所參考的所有 .dll, 而您所建立的元件將會在中繼資料中列出檔案作為元件參考。

如果檔案不包含元件 (如果檔案是模組), 而且您不想要在目前 (元件) 應用程式中使用模組的類型資訊, 您可以選擇只指出模組是元件的一部分;使用[/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)。 任何參考該組件的應用程式就可以使用模組的類型。

使用 **#using**的替代方法是[/FU](../build/reference/fu-name-forced-hash-using-file.md)編譯器選項。

傳遞給 **#using**的 .exe 元件應該使用其中一個 .net Visual Studio 編譯器 (例如 Visual Basic 或 Visual C#) 進行編譯。  嘗試從以 `/clr` 編譯的 .exe 組件匯入中繼資料，可能會產生檔案載入例外狀況。

> [!NOTE]
> 使用 **#using**所參考的元件, 可以使用在編譯時期匯入的不同檔案版本來執行, 導致用戶端應用程式產生非預期的結果。

為了讓編譯器能夠辨識元件中的型別 (而不是模組), 必須強制將它解析成型別。 例如, 您可以藉由定義類型的實例來強制執行。 還有其他方法可以解析編譯器元件中的型別名稱。 例如, 如果您從元件中的型別繼承, 則編譯器會知道型別名稱。

當匯入從使用[__declspec (thread)](../cpp/thread.md)的原始程式碼所建立的中繼資料時, 執行緒語義不會保存在中繼資料中。 例如, 以 **__declspec (thread)** 宣告的變數會在針對 .NET Framework common language runtime 建立的程式中編譯, 然後透過 **#using**匯入, 而不會在變數上有 **__declspec (thread)** 語義。

**#Using**所參考的檔案中, 所有匯入的類型 (managed 和 native) 都可以使用, 但是編譯器會將原生類型視為宣告, 而不是定義。

以 `/clr` 編譯時，mscorlib.dll 會自動參考。

當編譯器解析傳遞給 **#using**的檔案名時, LIBPATH 環境變數會指定要搜尋的目錄。

編譯器會搜尋下列路徑中的參考:

- 在 **#using**語句中指定的路徑。

- 目前的目錄。

- .NET Framework 系統目錄。

- 使用[/AI](../build/reference/ai-specify-metadata-directories.md)編譯器選項新增的目錄。

- LIBPATH 環境變數的目錄。

## <a name="example"></a>範例

如果您建立元件 (C) 並參考本身參考另一個元件 (A) 的元件 (B), 除非您明確地使用 C 中的其中一個類型, 否則不需要明確參考元件 A。

```cpp
// using_assembly_A.cpp
// compile with: /clr /LD
public ref class A {};
```

## <a name="example"></a>範例

```cpp
// using_assembly_B.cpp
// compile with: /clr /LD
#using "using_assembly_A.dll"
public ref class B {
public:
   void Test(A a) {}
   void Test() {}
};
```

## <a name="example"></a>範例

在下列範例中, 不會參考*using_assembly_A*, 因此沒有任何編譯器錯誤, 因為程式不會使用*using_assembly_A*中定義的任何類型。

```cpp
// using_assembly_C.cpp
// compile with: /clr
#using "using_assembly_B.dll"
int main() {
   B b;
   b.Test();
}
```

## <a name="see-also"></a>另請參閱

[預處理器指示詞](../preprocessor/preprocessor-directives.md)
