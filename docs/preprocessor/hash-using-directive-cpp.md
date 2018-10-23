---
title: '#using 指示詞 (C + + /cli CLI) |Microsoft Docs'
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- friend_as_cpp
- '#using'
- friend_as
- '#using_cpp'
dev_langs:
- C++
helpviewer_keywords:
- using directive (#using)
- '#using directive'
- LIBPATH environment variable
- preprocessor, directives
ms.assetid: 870b15e5-f361-40a8-ba1c-c57d75c8809a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 23e3447538590ec6a0e9392800bc6638900c6d6d
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808689"
---
# <a name="using-directive-ccli"></a>#using 指示詞 (C + + /cli CLI)

中繼資料匯入程式，以編譯[/clr](../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="syntax"></a>語法

```
#using file [as_friend]
```

### <a name="parameters"></a>參數

*file*<br/>
MSIL .dll、.exe、.netmodule 或 .obj。例如，套用至物件的

`#using <MyComponent.dll>`

*as_friend*<br/>
指定中的所有類型*檔案*存取。 如需詳細資訊，請參閱 < [Friend 組件 （c + +）](../dotnet/friend-assemblies-cpp.md)。

## <a name="remarks"></a>備註

*檔案*可以是其受管理的資料和 managed 的建構您匯入的 Microsoft intermediate language (MSIL) 檔案。 如果.dll 檔案包含組件資訊清單中，則會匯入資訊清單中所參考的所有.dll，而且您要建置的組件會列出*檔案*中做為組件參考的中繼資料。

如果*檔案*不包含組件 (如果*檔案*是模組)，如果您不打算使用目前 （組件） 應用程式中從模組的類型資訊，您可以選擇只表示模組屬於組件。使用  [/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)。 任何參考該組件的應用程式就可以使用模組的類型。

若要使用替代 **#using**是[/FU](../build/reference/fu-name-forced-hash-using-file.md)編譯器選項。

.exe 組件傳遞至 **#using**應該編譯使用其中一種.NET Visual Studio 編譯器 (Visual Basic 或 Visual C# 範例中）。  嘗試從以 `/clr` 編譯的 .exe 組件匯入中繼資料，可能會產生檔案載入例外狀況。

> [!NOTE]
> 參考使用的元件 **#using**可以執行在編譯時期，匯入的檔案，導致非預期的結果提供給用戶端應用程式的不同版本。

為了讓編譯器可辨識的組件 （而非模組） 中的型別，它必須強制解析的型別，您可以完成這件事，比方說，藉由定義類型的執行個體。 如果您繼承自組件中的型別，則需要有其他方法解決編譯器，例如，組件中的型別名稱，型別名稱會隨後即可得知給編譯器。

當匯入中繼資料從來源使用的程式碼建置[__declspec （thread)](../cpp/thread.md)，執行緒語意不會保存在中繼資料。 例如，以宣告的變數 **__declspec （thread)**，是針對.NET Framework common language runtime，組建，然後透過匯入的程式中編譯 **#using**，將不再有 **__declspec （thread)** 變數上的語意。

匯入中所參考的檔案類型 （managed 與原生） 的所有 **#using**可以使用，但是編譯器會將原生類型視為宣告不是定義。

以 `/clr` 編譯時，mscorlib.dll 會自動參考。

LIBPATH 環境變數指定的目錄，則會搜尋時，編譯器會嘗試解析檔案名稱傳遞給 **#using**。

編譯器會沿著下列路徑搜尋參考：

- 指定的路徑 **#using**陳述式。

- 目前的目錄。

- .NET Framework 系統目錄。

- 加上目錄[/AI](../build/reference/ai-specify-metadata-directories.md)編譯器選項。

- LIBPATH 環境變數的目錄。

## <a name="example"></a>範例

如果您建置組件 (C) 並參考組件 (B)，而其本身參考另一個組件 (A)，您不需要明確參考組件 A，除非您在 C 中明確使用 A 的類型。

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

在下列範例中，不參考 using_assembly_A.dll 並不會造成編譯錯誤，因為程式不會使用 using_assembly_A.cpp 中定義的任何類型。

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