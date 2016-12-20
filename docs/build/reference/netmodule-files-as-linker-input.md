---
title: ".netmodule 檔做為連結器輸入 | Microsoft Docs"
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
helpviewer_keywords: 
  - ".netmodule"
  - "連結 [C++], 模組"
  - "模組, Visual C++"
  - "MSIL 連結"
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
caps.latest.revision: 22
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .netmodule 檔做為連結器輸入
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

link.exe 現在接受 MSIL .obj 或 .netmodule 做為輸入。  連結器產生的輸出檔將是組件或 .netmodule 沒有在輸入至連結器的執行階段相依性任何 .obj 或 .netmodule。  
  
 .netmodule 是由 Visual C\+\+ 編譯器以 [\/LN \(建立 MSIL 模組\)](../../build/reference/ln-create-msil-module.md) 建立，或是由連結器以 [\/NOASSEMBLY \(建立 MSIL 模組\)](../../build/reference/noassembly-create-a-msil-module.md) 建立。.obj 永遠都是在 Visual C\+\+ 編譯中建立。  其他 Visual Studio 編譯器是使用 **\/target:module** 編譯器選項。  
  
 在大部分情況下，您必須傳遞給連結器從建立 .netmodule 的 Visual C\+\+ 編譯的 .obj 檔，除非 .netmodule 建立 [\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)。  MSIL .netmodule 必須是純 MSIL，可以由 Visual C\+\+ 編譯器使用 **\/clr:safe** 產生。  其他 Visual Studio 編譯器是預設為產生純 MSIL 模組。  
  
 如需如何從命令列叫用連結器的詳細資訊，請參閱[連結器命令列語法](../../build/reference/linker-command-line-syntax.md)和[設定命令列建置的路徑和環境變數](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。  
  
 傳遞 .netmodule 或 .dll 檔給由 Visual C\+\+ 編譯器以 **\/clr** 或是以 **\/clr:pure** 編譯的連結器可能會產生連結器錯誤。  如需詳細資訊，請參閱[選擇 .netmodule 輸入檔的格式](../../build/reference/choosing-the-format-of-netmodule-input-files.md)。  
  
 連結器接受原生 .obj 檔案以及用 **\/clr**、**\/clr:pure** 或 **\/clr:safe** 編譯的 MSIL .obj 檔案。  傳遞相同組建中的混合 .obj 時，所產生輸出檔案的可驗證性將預設為相當於輸入模組最低層級的可驗證性。  例如，如果您傳遞安全的純 .obj 給連結器，輸出檔案將會是純檔案。  [\/CLRIMAGETYPE \(指定 CLR 映像類型\)](../../build/reference/clrimagetype-specify-type-of-clr-image.md) 可讓您指定較低層級可驗證性，以配合您的需要。  
  
 如果您目前擁有由兩個或兩個以上組件組成的應用程式，而您要讓應用程式包含在一個組件中，您必須重新編譯組件，然後連結 .obj 或 .netmodules來產生單一組件。  
  
 您必須在建立可執行檔映像時，使用 [\/ENTRY \(進入點符號\)](../../build/reference/entry-entry-point-symbol.md) 指定進入點。  
  
 當連接與 MSIL .obj 或 .netmodule 檔案，請使用 [\/LTCG \(連結時間產生程式碼\)](../../build/reference/ltcg-link-time-code-generation.md)，則為，否則當連結器遭遇 MSIL .obj 或 .netmodule 時，它將會重新啟動與 \/LTCG 的連結。  
  
 MSIL .obj 或 .netmodule 檔案也可以傳遞給 cl.exe。  
  
 輸入 MSIL .obj 或 .netmodule 檔案無法具有內嵌資源。  資源是以 [\/ASSEMBLYRESOURCE \(內嵌 Managed 資源\)](../../build/reference/assemblyresource-embed-a-managed-resource.md) 連結器選項，或以 **\/resource** 編譯器選項，在其他 Visual Studio 編譯器中內嵌於輸出檔案中 \(模組或組件\)。  
  
 執行 MSIL 連結時，而且如果不同時指定 [\/LTCG \(連結時間產生程式碼\)](../../build/reference/ltcg-link-time-code-generation.md)，將會看到報告連結重新啟動的資訊訊息。  這項訊息可加以忽略，但若要以 MSIL 連結改進連結器效能，請明確指定 **\/LTCG**。  
  
## 範例  
 在 C\+\+ 程式碼中，會針對非系統例外狀況叫用對應 try 的 catch 區塊。  但是，CLR 預設會以 <xref:System.Runtime.CompilerServices.RuntimeWrappedException> 包裝非系統例外狀況。  從 Visual C\+\+ 和非 Visual C\+\+ 模組建立組件，而且當 try 區塊擲回非系統例外狀況時，您希望從 C\+\+ 程式碼中 catch 區塊的對應 try 子句中叫用此區塊時，則必須針對 C\+\+ 模組將  
  
 \[assembly:System::Runtime::CompilerServices::RuntimeCompatibility\(WrapNonExceptionThrows\=false\)\] 屬性加入到原始程式碼中。  
  
```  
// MSIL_linking.cpp  
// compile with: /c /clr  
value struct V {};  
  
ref struct MCPP {  
   static void Test() {  
      try {  
         throw (gcnew V);  
      }  
      catch (V ^) {  
         System::Console::WriteLine("caught non System exception in C++ source code file");  
      }  
   }  
};  
  
/*  
int main() {  
   MCPP::Test();  
}  
*/  
```  
  
## 範例  
 可藉由變更 WrapNonExceptionThrows 屬性的布林值，修改 Visual C\+\+ 程式碼攔截非系統例外狀況的能力。  
  
```  
// MSIL_linking_2.cs  
// compile with: /target:module /addmodule:MSIL_linking.obj  
// post-build command: link /LTCG MSIL_linking.obj MSIL_linking_2.netmodule /entry:MLinkTest.Main /out:MSIL_linking_2.exe /subsystem:console  
using System.Runtime.CompilerServices;  
  
// enable non System exceptions  
[assembly:RuntimeCompatibility(WrapNonExceptionThrows=false)]  
  
class MLinkTest {  
   public static void Main() {  
      try {  
         MCPP.Test();  
      }  
      catch (RuntimeWrappedException) {  
         System.Console.WriteLine("caught a wrapped exception in C#");  
      }  
   }  
}  
```  
  
  **在 C\+\+ 原始程式碼檔中攔截到的非系統例外狀況**   
## 請參閱  
 [LINK 輸入檔](../../build/reference/link-input-files.md)   
 [連結器選項](../../build/reference/linker-options.md)