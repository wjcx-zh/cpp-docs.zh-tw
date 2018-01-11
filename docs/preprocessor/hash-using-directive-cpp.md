---
title: "#<a name=\"using-directive-cclr--microsoft-docs\"></a>using 指示詞 (C + + CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- friend_as_cpp
- '#using'
- friend_as
- '#using_cpp'
dev_langs: C++
helpviewer_keywords:
- using directive (#using)
- '#using directive'
- LIBPATH environment variable
- preprocessor, directives
ms.assetid: 870b15e5-f361-40a8-ba1c-c57d75c8809a
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a8a73eb8e9b5c3f3ba67e4466a6e7138010fd430
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-directive-cclr"></a>#using 指示詞 (C + + CLR)
中繼資料匯入編譯的程式[/clr](../build/reference/clr-common-language-runtime-compilation.md)。  
  
## <a name="syntax"></a>語法  
  
```  
#using file [as_friend]  
```  
  
#### <a name="parameters"></a>參數  
 `file`  
 MSIL .dll、.exe、.netmodule 或 .obj。例如，套用至物件的  
  
 `#using <MyComponent.dll>`  
  
 as_friend  
 指定在 `file` 中的所有類型都是可存取的。  如需詳細資訊，請參閱[Friend 組件 （c + +）](../dotnet/friend-assemblies-cpp.md)。  
  
## <a name="remarks"></a>備註  
 `file` 可以是您為其 Managed 資料和 Managed 建構，而匯入的 Microsoft Intermediate Language (MSIL) 檔案。 如果.dll 檔案包含組件資訊清單，則會匯入所有資訊清單中所參考的 dll，而且您要建置的組件會列出*檔案*中做為組件參考的中繼資料。  
  
 如果`file`不包含組件 (如果`file`是模組)，如果您不想使用目前 （組件） 應用程式中從模組的類型資訊，您可以選擇只表示模組一部分之組件; 請改用[/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)。 任何參考該組件的應用程式就可以使用模組的類型。  
  
 若要使用替代`#using`是[/FU](../build/reference/fu-name-forced-hash-using-file.md)編譯器選項。  
  
 .exe 組件傳遞至`#using`應該編譯使用其中一種.NET Visual Studio 編譯器編譯 (Visual Basic 或 Visual C# 中，例如）。  嘗試使用編譯的.exe 組件從匯入中繼資料**/clr**會導致檔案載入例外狀況。  
  
> [!NOTE]
>  以 `#using` 參考的元件可以與編譯時匯入不同版本的檔案執行，導致用戶端應用程式產生未預期的結果。  
  
 為了讓編譯器可以辨認組件 （而非模組） 中的型別，它需要強制解析類型，您可以執行，例如，藉由定義類型的執行個體。 如果您繼承自類型的組件中沒有其他方法解決編譯器，例如，組件中的型別名稱，型別名稱會隨後即可得知編譯器。  
  
 匯入從使用的原始程式碼建置的中繼資料時[__declspec （thread)](../cpp/thread.md)，執行緒語意不會保存在中繼資料。 例如，宣告變數**__declspec （thread)**、 已編譯的.NET Framework common language runtime 的組建，然後再匯入透過程式中`#using`，將不再有**__declspec (執行緒）**變數上的語意。  
  
 在 `#using` 所參考的檔案中，所有匯入的類型 (Managed 和原生) 都是可用的，不過，編譯器會將原生類型視為宣告而不是定義。  
  
 編譯時，會自動參考 mscorlib.dll **/clr**。  
  
 當編譯器嘗試解析傳遞至 `#using` 的檔案名稱時，LIBPATH 環境變數會指定要搜尋的目錄。  
  
 編譯器會沿著下列路徑搜尋參考：  
  
-   在 `#using` 陳述式中指定的路徑。  
  
-   目前的目錄。  
  
-   .NET Framework 系統目錄。  
  
-   與所加入的目錄[/AI](../build/reference/ai-specify-metadata-directories.md)編譯器選項。  
  
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
  
## <a name="see-also"></a>請參閱  
 [前置處理器指示詞](../preprocessor/preprocessor-directives.md)