---
title: '#using 指示詞 (C + + /cli CLI) |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: c2255f5de9cc26505bb07110da6368a039009c6c
ms.sourcegitcommit: b8b1cba85ff423142d73c888be26baa8c33f3cdc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093029"
---
# <a name="using-directive-ccli"></a>#using 指示詞 (C + + /cli CLI)
中繼資料匯入程式，以編譯[/clr](../build/reference/clr-common-language-runtime-compilation.md)。  
  
## <a name="syntax"></a>語法  
  
```  
#using file [as_friend]  
```  
  
#### <a name="parameters"></a>參數  
 `file`  
 MSIL .dll、.exe、.netmodule 或 .obj。例如，套用至物件的  
  
 `#using <MyComponent.dll>`  
  
 as_friend  
 指定在 `file` 中的所有類型都是可存取的。  如需詳細資訊，請參閱 < [Friend 組件 （c + +）](../dotnet/friend-assemblies-cpp.md)。  
  
## <a name="remarks"></a>備註  
 `file` 可以是您為其 Managed 資料和 Managed 建構，而匯入的 Microsoft Intermediate Language (MSIL) 檔案。 如果.dll 檔案包含組件資訊清單中，則會匯入資訊清單中所參考的所有.dll，而且您要建置的組件會列出*檔案*中做為組件參考的中繼資料。  
  
 如果`file`不包含組件 (如果`file`是模組) 而且如果您不打算使用目前 （組件） 應用程式中從模組的類型資訊，則可以選擇指定模組是屬於組件; 請改用[/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)。 任何參考該組件的應用程式就可以使用模組的類型。  
  
 若要使用替代`#using`已[/FU](../build/reference/fu-name-forced-hash-using-file.md)編譯器選項。  
  
 .exe 組件傳遞至`#using`應該編譯使用其中一種.NET Visual Studio 編譯器 (Visual Basic 或 Visual C# 範例中）。  嘗試從編譯的.exe 組件匯入中繼資料 **/clr**會導致檔案載入例外狀況。  
  
> [!NOTE]
>  以 `#using` 參考的元件可以與編譯時匯入不同版本的檔案執行，導致用戶端應用程式產生未預期的結果。  
  
 為了讓編譯器可辨識的組件 （而非模組） 中的型別，它必須強制解析的型別，您可以完成這件事，比方說，藉由定義類型的執行個體。 如果您繼承自組件中的型別，則需要有其他方法解決編譯器，例如，組件中的型別名稱，型別名稱會隨後即可得知給編譯器。  
  
 當匯入中繼資料從來源使用的程式碼建置[__declspec （thread)](../cpp/thread.md)，執行緒語意不會保存在中繼資料。 例如，以宣告的變數 **__declspec （thread)**，是針對.NET Framework common language runtime，組建，然後透過匯入的程式中編譯`#using`，將不再有 **__declspec (執行緒）** 變數上的語意。  
  
 在 `#using` 所參考的檔案中，所有匯入的類型 (Managed 和原生) 都是可用的，不過，編譯器會將原生類型視為宣告而不是定義。  
  
 進行編譯時，會自動參考 mscorlib.dll **/clr**。  
  
 當編譯器嘗試解析傳遞至 `#using` 的檔案名稱時，LIBPATH 環境變數會指定要搜尋的目錄。  
  
 編譯器會沿著下列路徑搜尋參考：  
  
-   在 `#using` 陳述式中指定的路徑。  
  
-   目前的目錄。  
  
-   .NET Framework 系統目錄。  
  
-   加上目錄[/AI](../build/reference/ai-specify-metadata-directories.md)編譯器選項。  
  
-   LIBPATH 環境變數的目錄。  
  
## <a name="example"></a>範例  
 如果您建置組件 (C) 並參考組件 (B)，而其本身參考另一個組件 (A)，您不需要明確參考組件 A，除非您在 C 中明確使用 A 的類型。  
  
```  
// using_assembly_A.cpp  
// compile with: /clr /LD  
public ref class A {};  
```  
  
## <a name="example"></a>範例  
  
```  
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
  
```  
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
