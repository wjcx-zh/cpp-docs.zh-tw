---
title: "#using 指示詞 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "friend_as_cpp"
  - "#using"
  - "friend_as"
  - "#using_cpp"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#using 指示詞"
  - "LIBPATH 環境變數"
  - "前置處理器, 指示詞"
  - "using 指示詞 (#using)"
ms.assetid: 870b15e5-f361-40a8-ba1c-c57d75c8809a
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #using 指示詞 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將中繼資料匯入程式以 [\/clr](../build/reference/clr-common-language-runtime-compilation.md)編譯。  
  
## 語法  
  
```  
#using file [as_friend]  
```  
  
#### 參數  
 `file`  
 MSIL .dll、.exe、.netmodule 或 .obj。  例如：  
  
 `#using <MyComponent.dll>`  
  
 as\_friend  
 指定所有在 `file` 中的型別都可以存取。如需詳細資訊，請參閱[Friend 組件 \(C\+\+\)](../dotnet/friend-assemblies-cpp.md)。  
  
## 備註  
 `file` 可以是您為其管理的資料和 Managed 建構匯入的 Microsoft Intermediate Language \(MSIL\) 檔案。  如果 .dll 檔案包含組件資訊清單，則會匯入資訊清單所參考的所有 .dll ，並會列出做為組件參考的中繼資料*檔案*的組件。  
  
 如果 `file` 不包含組件 \(如果 `file` 是模組\)，如果您在目前 \(組件\) 應用程式不打算使用模組的型別資訊，您可以指定的選項模組做為組件;使用 [\/組件模組](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)。  模組中的型別在任何跟組件相關的應用程式中皆可使用  
  
 使用 `#using` 的替代方案是 [\/FU](../build/reference/fu-name-forced-hash-using-file.md) 編譯器選項。  
  
 .exe 組件傳遞給 `#using` 應該編譯與 **\/clr:safe** 或 **\/clr:pure**，或與其他 Visual Studio 編譯器 \(例如 Visual Basic 或 Visual C\#，\)。嘗試從 .exe 組件的中繼資料編譯 **\/clr** 可能會產生檔案載入的例外狀況。  
  
> [!NOTE]
>  參考與 `#using` 的元件在編譯時可以執行不同版本的匯入檔案，導致用戶端的應用程式產生無法預期的結果。  
  
 如果要讓編譯器辨認組件 \(而非模組\) 中的某個型別，就必須強制它解析這個型別，您可以藉由定義該型別的執行個體來進行這種強制解析。  還有其他方法可以為編譯器解析決組件中的型別名稱，例如，如果您是從組件中的型別繼承，編譯器隨後即可得知型別名稱。  
  
 當將使用 [declspec\(thread\)](../cpp/thread.md)中的原始程式碼建立的中繼資料，執行緒語意在中繼資料不會保存。  例如，透過 `#using`宣告 **\_\_declspec\(thread\)**變數時，編譯為 .NET Framework 的 Common Language Runtime 建置的程式，然後匯入的變數，將不再有變數的 **\_\_declspec\(thread\)** 語意。  
  
 所有匯入的型別 \(Managed 和原生\) 在參考 `#using` 的檔案是可用的，不過，編譯器會將原生型別視為宣告而不是定義。  
  
 在以 **\/clr**編譯時， mscorlib.dll 會自動參考。  
  
 當編譯器嘗試解析檔案名稱並傳遞至 `#using`時，LIBPATH 環境變數會指定要搜尋的目錄。  
  
 編譯器會搜尋下列參考路徑:  
  
-   在陳述式 `#using` 中指定的路徑。  
  
-   目前的目錄。  
  
-   .NET Framework 系統目錄。  
  
-   目錄中加入 [\/AI](../build/reference/ai-specify-metadata-directories.md) 編譯器選項。  
  
-   在環境變數 LIBPATH 的目錄。  
  
## 範例  
 如果您建立組件 \(c\) 並參考本身有參考組件\(A\)的組件\(B\)，您不需要明確參考組件 A，除非您明確在C之中使用A裡面的型別。  
  
```  
// using_assembly_A.cpp  
// compile with: /clr /LD  
public ref class A {};  
```  
  
## 範例  
  
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
  
## 範例  
 在下列範例中，不參考using\_assembly\_A.dll並不是造成沒有編譯錯誤的原因，而是因為程式中沒有使用任何在using\_assembly\_A.cpp裡面定義的型別。  
  
```  
// using_assembly_C.cpp  
// compile with: /clr  
#using "using_assembly_B.dll"  
int main() {  
   B b;  
   b.Test();  
}  
```  
  
## 請參閱  
 [前置處理器指示詞](../preprocessor/preprocessor-directives.md)