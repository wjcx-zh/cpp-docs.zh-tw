---
title: '#using 指示詞 (C++/CLI)'
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
ms.openlocfilehash: 0245eb15219585421be83def0258415ab4b573b6
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684257"
---
# <a name="using-directive-ccli"></a>#using 指示詞 (c + +/CLI) 

將中繼資料匯入以 [/clr](../build/reference/clr-common-language-runtime-compilation.md)編譯的程式。

## <a name="syntax"></a>語法

> **`#using`***file* [ **`as_friend`** ]

### <a name="parameters"></a>參數

*檔*\
Microsoft 中繼語言 (MSIL) *`.dll`* 、、 *`.exe`* 或檔案 *`.netmodule`* *`.obj`* 。 例如，

`#using <MyComponent.dll>`

**`as_friend`**\
指定檔案中的所有類型 *都可以存取* 。 如需詳細資訊，請參閱 [ (c + +) 的 Friend 元件 ](../dotnet/friend-assemblies-cpp.md)。

## <a name="remarks"></a>備註

檔案*可以是*您針對其 managed 資料和 managed 結構匯入之 Microsoft 中繼語言 (MSIL) 檔。 如果 DLL 包含組件資訊清單，則會匯入資訊清單中所參考的所有 Dll。 您所建立的元件將會 *以元件* 參考的形式列出中繼資料中的檔案。

也許*檔案**不包含元件 (檔案*是模組) ，而且您不想要在目前 (元件) 應用程式中使用模組的類型資訊。 您可以使用 [/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)，表示模組是元件的一部分。 任何參考該組件的應用程式就可以使用模組的類型。

使用的替代方案 **`#using`** 是 [/FU](../build/reference/fu-name-forced-hash-using-file.md) 編譯器選項。

傳遞給的 .exe 元件 **`#using`** 應該使用其中一種 .net Visual Studio 編譯器 (Visual Basic 或 Visual c #，例如) 。  嘗試從以編譯的 .exe 元件匯入中繼資料， **`/clr`** 將會導致檔案載入例外狀況。

> [!NOTE]
> 參考的元件 **`#using`** 可以使用在編譯時期匯入之不同版本的檔案執行，導致用戶端應用程式提供非預期的結果。

為了讓編譯器辨識元件中的型別 (不是模組) ，它需要強制解析型別。 您可以藉由定義型別的實例來強制執行。 有其他方法可以解決編譯器元件中的型別名稱。 例如，如果您繼承自元件中的型別，編譯器就會知道型別名稱。

從使用的原始程式碼匯入建立的中繼資料時 [`__declspec(thread)`](../cpp/thread.md) ，執行緒語義不會保存在中繼資料中。 例如，使用宣告的變數 **`__declspec(thread)`** ，在為 .NET Framework 通用語言執行時間建立的程式中編譯，然後透過匯入，在 **`#using`** 變數上不會有 **`__declspec(thread)`** 語義。

所有匯入的類型 (所參考之檔案中的 managed 和原生) **`#using`** 都可使用，但編譯器會將原生類型視為宣告，而不是定義。

使用編譯時，會自動參考 mscorlib.dll **`/clr`** 。

當編譯器解析傳遞給的檔案名時，LIBPATH 環境變數會指定要搜尋的目錄 **`#using`** 。

編譯器會在下列路徑搜尋參考：

- 語句中指定的路徑 **`#using`** 。

- 目前的目錄。

- .NET Framework 系統目錄。

- 使用編譯器選項加入的目錄 [`/AI`](../build/reference/ai-specify-metadata-directories.md) 。

- LIBPATH 環境變數的目錄。

## <a name="examples"></a>範例

您可以建立參考第二個元件的元件，而該元件本身會參考第三個元件。 如果您明確地使用其中一個類型，您只需要明確參考第一個元件的第一個元件。

```cpp
// using_assembly_A.cpp
// compile with: /clr /LD
public ref class A {};
```

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

在下列範例中，編譯器並不會回報參考 *using_assembly_A.dll*的相關錯誤，因為該程式不會使用 *using_assembly_A .cpp*中定義的任何類型。

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

[前置處理器指示詞](../preprocessor/preprocessor-directives.md)
