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
ms.openlocfilehash: 0da255957e92a570750da2687bf1444df2e6ab13
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219426"
---
# <a name="using-directive-ccli"></a>#using 指示詞（c + +/CLI）

將中繼資料匯入使用[/clr](../build/reference/clr-common-language-runtime-compilation.md)編譯的程式。

## <a name="syntax"></a>語法

> **`#using`***file*檔案 [ **`as_friend`** ]

### <a name="parameters"></a>參數

*文字檔*\
Microsoft 中繼語言（MSIL） *`.dll`* 、、 *`.exe`* 或檔案 *`.netmodule`* *`.obj`* 。 例如

`#using <MyComponent.dll>`

**`as_friend`**\
指定檔案中的所有類型*都可以存取*。 如需詳細資訊，請參閱[Friend 元件（c + +）](../dotnet/friend-assemblies-cpp.md)。

## <a name="remarks"></a>備註

檔案可以是 Microsoft 中繼語言（MSIL）檔案，*您可以為*其管理的資料和受控結構匯入該檔案。 如果 DLL 包含組件資訊清單，則會匯入資訊清單中參考的所有 Dll。 您所建立的元件將會在元*資料中列出*檔案，做為元件參考。

也許*檔案**不包含元件（檔案*是模組），而且您不想要在目前（元件）應用程式中使用模組的型別資訊。 您可以使用[/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)指出模組是元件的一部分。 任何參考該組件的應用程式就可以使用模組的類型。

使用的替代方法 **`#using`** 是[/FU](../build/reference/fu-name-forced-hash-using-file.md)編譯器選項。

傳遞給的 .exe 元件 **`#using`** 應該使用其中一個 .net Visual Studio 編譯器（例如 Visual Basic 或 Visual c #）進行編譯。  嘗試從以編譯的 .exe 元件匯入中繼資料 **`/clr`** 將會導致檔案載入例外狀況。

> [!NOTE]
> 使用所參考的元件 **`#using`** ，可以在編譯時期匯入不同版本的檔案執行，導致用戶端應用程式提供非預期的結果。

為了讓編譯器能夠辨識元件中的型別（而不是模組），必須強制將它解析成型別。 例如，您可以藉由定義類型的實例來強制執行。 還有其他方法可以解析編譯器元件中的型別名稱。 例如，如果您從元件中的型別繼承，則編譯器會知道型別名稱。

當匯入從使用的原始程式碼所建立的中繼資料時 [`__declspec(thread)`](../cpp/thread.md) ，執行緒語義不會保存在中繼資料中。 例如，以宣告的變數 **`__declspec(thread)`** 會在針對 .NET Framework common language runtime 建立的程式中編譯，然後透過匯入 **`#using`** ，在變數上不會有任何 **`__declspec(thread)`** 語義。

在所參考的檔案中，所有匯入的類型（managed 和 native） **`#using`** 都可以使用，但是編譯器會將原生類型視為宣告，而不是定義。

使用進行編譯時，會自動參考 mscorlib.dll **`/clr`** 。

當編譯器解析傳遞至的檔案名時，LIBPATH 環境變數會指定要搜尋的目錄 **`#using`** 。

編譯器會搜尋下列路徑中的參考：

- 語句中指定的路徑 **`#using`** 。

- 目前的目錄。

- .NET Framework 系統目錄。

- 使用編譯器選項新增的目錄 [`/AI`](../build/reference/ai-specify-metadata-directories.md) 。

- LIBPATH 環境變數的目錄。

## <a name="example"></a>範例

您可以建立一個元件，參考第二個元件，其本身會參考第三個元件。 如果您明確使用其中一個類型，您只需要從第一個元件明確參考第三個元件。

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

在下列範例中，編譯器不會報告有關參考*using_assembly_A.dll*的錯誤，因為程式不會使用*using_assembly_A*中定義的任何類型。

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
